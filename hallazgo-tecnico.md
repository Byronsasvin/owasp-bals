# DOCUMENTACIÓN TÉCNICA DE HALLAZGO DE SEGURIDAD

---

## INFORMACIÓN DEL HALLAZGO

**ID**: [OWASP-001-APP-001]  
**Título**: [Nombre del hallazgo]  
**Vector OWASP**: A01:2021 - Injection  
**CVSS v3.1**: 9.8  
**Severidad**: CRITICAL  
**CWE**: CWE-89  
**CAPEC**: CAPEC-66  

---

## VECTOR CVSS COMPLETO

**String**: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H

| Componente | Valor | Descripción |
|-----------|-------|-------------|
| AV | Network | Atacante puede explotar remotamente |
| AC | Low | No requiere condiciones especiales |
| PR | None | No requiere autenticación |
| UI | None | No requiere interacción del usuario |
| S | Unchanged | Impacto limitado al contexto vulnerable |
| C | High | Confidencialidad completamente comprometida |
| I | High | Integridad completamente comprometida |
| A | High | Disponibilidad completamente comprometida |

**Score**: 9.8 = CRITICAL

---

## DESCRIPCIÓN TÉCNICA

### Resumen

Breve descripción del hallazgo (1-2 párrafos).

### Contexto

Explicar dónde y cómo ocurre la vulnerabilidad en el código/aplicación.

### Causa Raíz

Análisis técnico de por qué existe la vulnerabilidad.

---

## UBICACIÓN DEL HALLAZGO

**Endpoint**: POST /api/search  
**Parámetro**: q=  
**Tipo**: Query String  
**Método HTTP**: POST  
**Autenticación**: No requerida  
**Método de Autenticación (si aplica)**: N/A  

### URL Completa
```
POST https://app.com/api/search?q=[PAYLOAD]
Content-Type: application/json
```

---

## REPRODUCCIÓN

### Paso a Paso

1. Acceder a: https://app.com/api/search
2. Enviar parámetro: q=test' OR '1'='1
3. Observar respuesta: [Resultado esperado]

### Herramientas Utilizadas

- Burp Suite Community
- curl
- OWASP ZAP

### Comandos de Prueba

```bash
# Usando curl
curl -X POST "https://app.com/api/search" \
  -H "Content-Type: application/json" \
  -d '{"q":"test\" OR \"1\"=\"1\"}'

# Usando Burp intruder
[Configurar payload en parámetro q]
```

---

## EVIDENCE TÉCNICA

### Payload 1: Basic SQL Injection

```sql
' OR '1'='1' --
```

**Respuesta del servidor**:
```json
{
  "status": "success",
  "results": [
    {"id": 1, "name": "User1"},
    {"id": 2, "name": "User2"},
    {"id": 3, "name": "User3"}
  ]
}
```

**Análisis**: La aplicación retornó todos los registros, confirmando la inyección SQL.

### Payload 2: UNION-based SQL Injection

```sql
' UNION SELECT username,password FROM users --
```

**Respuesta del servidor**:
```json
{
  "username": "admin",
  "password": "hashed_password_here"
}
```

**Análisis**: Extracción de credenciales de administrador.

### Payload 3: Time-based Blind SQL Injection

```sql
' AND SLEEP(5) --
```

**Respuesta**: Retraso de 5 segundos confirmando la vulnerabilidad.

---

## FLUJO DE DATOS

```
User Input
    ↓
[q=test' OR '1'='1]
    ↓
SQL Query Construction
    ↓
query = "SELECT * FROM users WHERE name = '" + input + "'"
    ↓
Ejecución en Base de Datos
    ↓
Respuesta: [TODOS LOS USUARIOS]
```

---

## IMPACTO TÉCNICO

### Confidencialidad: HIGH
- Acceso no autorizado a datos de usuarios
- Exposición de hashes de contraseña
- Acceso a datos de negocio

### Integridad: HIGH
- Capacidad de modificar datos en base de datos
- Potencial para insertar/actualizar/eliminar registros
- Corrupción de integridad de datos

### Disponibilidad: HIGH
- Capacidad de eliminar tablas
- Acceso de recursos de base de datos
- Potencial DoS

---

## IMPACTO EN NEGOCIO

### Riesgos de Compliance

- **GDPR**: Violación de artículos 5, 32, 33
- **PCI-DSS**: Violación de 6.5.1 (Injection flaws)
- **HIPAA**: Violación de Technical Safeguards
- **CCPA**: Violación de data protection requirements

### Impacto Financiero

- Multas regulatorias: $500K - $2M+ (GDPR)
- Costo de breach notification: $100K - $500K+
- Reputación y pérdida de confianza: [Variable]
- Costo de remediation: $50K - $200K+

### Impacto Operacional

- Interrupción de servicio potencial
- Pérdida de datos críticos
- Compromiso de seguridad de datos de usuarios

---

## REMEDIACIÓN

### Solución Recomendada: Prepared Statements

#### Antes (Vulnerable)

```python
# Python - Flask
@app.route('/api/search', methods=['POST'])
def search():
    q = request.json['q']
    # VULNERABLE: Concatenación directa
    query = f"SELECT * FROM users WHERE name = '{q}'"
    results = db.query(query)
    return jsonify(results)
```

#### Después (Seguro)

```python
# Python - Flask con SQLAlchemy
@app.route('/api/search', methods=['POST'])
def search():
    q = request.json['q']
    # SEGURO: Prepared statement
    query = "SELECT * FROM users WHERE name = ?"
    results = db.query(query, (q,))
    return jsonify(results)

# Usando SQLAlchemy ORM (Recomendado)
from sqlalchemy import text

@app.route('/api/search', methods=['POST'])
def search():
    q = request.json['q']
    query = text("SELECT * FROM users WHERE name = :name")
    results = db.execute(query, {"name": q})
    return jsonify(results)
```

#### Código Node.js

```javascript
// Antes (Vulnerable)
app.post('/api/search', (req, res) => {
  const q = req.body.q;
  const query = `SELECT * FROM users WHERE name = '${q}'`;
  db.query(query, (err, results) => {
    res.json(results);
  });
});

// Después (Seguro)
app.post('/api/search', (req, res) => {
  const q = req.body.q;
  const query = "SELECT * FROM users WHERE name = ?";
  db.query(query, [q], (err, results) => {
    res.json(results);
  });
});
```

#### Código Java

```java
// Antes (Vulnerable)
String query = "SELECT * FROM users WHERE name = '" + q + "'";
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery(query);

// Después (Seguro)
String query = "SELECT * FROM users WHERE name = ?";
PreparedStatement stmt = conn.prepareStatement(query);
stmt.setString(1, q);
ResultSet rs = stmt.executeQuery();
```

### Pasos de Implementación

1. **Analysis** (2h)
   - Identificar todos los puntos de inyección
   - Mapear impacto de cambios
   - Planificar implementación

2. **Development** (6h)
   - Implementar prepared statements
   - Actualizar todas las queries afectadas
   - Code review

3. **Testing** (4h)
   - Testing funcional
   - Verificar no regresiones
   - Security testing post-fix

4. **Deployment** (2h)
   - Desplegar a staging
   - Re-testing en staging
   - Deploy a producción

5. **Validation** (2h)
   - Ejecutar payload de prueba
   - Verificar fix completo
   - Documentación

**Total estimado**: 16 horas

---

## VALIDACIÓN POST-REMEDIACIÓN

### Pruebas Funcionales

```bash
# El payload ya NO debe funcionar
curl -X POST "https://app.com/api/search" \
  -d "q=test' OR '1'='1"

# Debe retornar: No results (no todos los usuarios)
# NO debe retornar: Todos los usuarios
```

### Fuzzing Testing

Usar payloads estándar OWASP:
- `' OR '1'='1`
- `' UNION SELECT NULL,NULL --`
- `'; DROP TABLE users; --`
- `test' AND '1'='1`
- `test' AND 1=1 --`

### SAST Scanning

```bash
# Python
bandit -r . --severity high

# Node.js
eslint . --ext .js

# Java
mvn dependency-check:check
```

### Herramientas Automatizadas

- OWASP ZAP SQL Injection scanner
- Burp Suite SQL Injection test
- Nuclei template: sql-injection

---

## REFERENCIAS

### OWASP
- [OWASP SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
- [OWASP Testing Guide - SQL Injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05-Testing_for_SQL_Injection)

### Standards
- [CWE-89: SQL Injection](https://cwe.mitre.org/data/definitions/89.html)
- [CAPEC-66: SQL Injection](https://capec.mitre.org/data/definitions/66.html)
- [NIST SP 800-53: SI-10](https://nvlpubs.nist.gov/)

### Herramientas
- [OWASP ZAP](https://www.zaproxy.org/)
- [Burp Suite](https://portswigger.net/burp)
- [sqlmap](http://sqlmap.org/)

---

## APROBACIÓN

**Evaluador**: [Nombre]  
**Fecha**: ___________  

**Revisado por**: [Security Manager]  
**Fecha**: ___________  

**Aprobado por**: [CTO/Director]  
**Fecha**: ___________  

---

*Confidencial - Distribución restringida*

---

**OWASP BALS v1.0.0** | Desarrollado por Byron Antonio Lainez Sasvin  
GitHub: [@Byronsasvin](https://github.com/Byronsasvin) | Email: [security@byronlainez.click](mailto:security@byronlainez.click)  
Website: [byronlainez.click](https://byronlainez.click) | Twitter: [@bals.sec](https://x.com/bals.sec)

