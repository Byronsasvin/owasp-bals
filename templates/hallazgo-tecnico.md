# DOCUMENTACIÓN TÉCNICA DE HALLAZGO DE SEGURIDAD

---

## INFORMACIÓN DEL HALLAZGO

**ID**: [OWASP-XXX-APP-001]  
**Título**: [Nombre descriptivo del hallazgo]  
**Vector OWASP**: A0X:2021 - [Nombre del Vector]  
**CVSS v3.1**: [Score]  
**Severidad**: [CRITICAL / HIGH / MEDIUM / LOW]  
**CWE**: CWE-[número]  
**CAPEC**: CAPEC-[número]  

---

## VECTOR CVSS COMPLETO

**String**: `CVSS:3.1/AV:[X]/AC:[X]/PR:[X]/UI:[X]/S:[X]/C:[X]/I:[X]/A:[X]`

| Componente | Valor | Descripción |
|-----------|-------|-------------|
| AV | [Network/Adjacent/Local/Physical] | [Descripción] |
| AC | [Low/High] | [Descripción] |
| PR | [None/Low/High] | [Descripción] |
| UI | [None/Required] | [Descripción] |
| S | [Unchanged/Changed] | [Descripción] |
| C | [None/Low/High] | [Descripción] |
| I | [None/Low/High] | [Descripción] |
| A | [None/Low/High] | [Descripción] |

**Score Final**: [X.X] = [SEVERIDAD]

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

**Endpoint**: [Método] [Ruta]  
**Parámetro vulnerable**: [nombre del parámetro]  
**Tipo de parámetro**: [Query String / Body / Header / Cookie]  
**Método HTTP**: [GET / POST / PUT / DELETE]  
**Autenticación requerida**: [Sí / No]  

### URL Completa

```
[MÉTODO] https://[host]/[ruta]
Content-Type: [tipo]

[body si aplica]
```

---

## PASOS DE REPRODUCCIÓN

1. [Paso 1]
2. [Paso 2]
3. [Paso 3 — observar resultado]

### Herramientas Utilizadas

- [Herramienta 1]
- [Herramienta 2]

### Comando de Prueba

```bash
# Ejemplo con curl
curl -X POST "https://[host]/[ruta]" \
  -H "Content-Type: application/json" \
  -d '[payload aquí]'
```

---

## EVIDENCIA TÉCNICA

### Payload de Prueba

```
[Insertar payload]
```

**Respuesta del servidor**:
```
[Insertar respuesta]
```

**Análisis**: [Explicar por qué la respuesta confirma la vulnerabilidad]

---

## FLUJO DE DATOS VULNERABLE

```
Input del Usuario
       ↓
[Parámetro no sanitizado]
       ↓
[Procesamiento inseguro]
       ↓
[Resultado peligroso]
```

---

## IMPACTO

### Técnico

- **Confidencialidad**: [ALTO/MEDIO/BAJO] — [Descripción]
- **Integridad**: [ALTO/MEDIO/BAJO] — [Descripción]
- **Disponibilidad**: [ALTO/MEDIO/BAJO] — [Descripción]

### Negocio

- Riesgo de [exposición de datos / interrupción / fraude]
- Violación potencial de [GDPR Art. X / PCI-DSS 6.5.X / HIPAA]
- Impacto financiero estimado: $[rango]

---

## REMEDIACIÓN

### Solución Recomendada

#### Antes (Vulnerable)

```[lenguaje]
// Código vulnerable aquí
```

#### Después (Seguro)

```[lenguaje]
// Código corregido aquí
```

### Pasos de Implementación

1. **Análisis** (Xh): Identificar todas las instancias afectadas
2. **Desarrollo** (Xh): Implementar la corrección
3. **Testing** (Xh): Pruebas funcionales y de seguridad
4. **Deployment** (Xh): Desplegar a producción
5. **Validación** (Xh): Confirmar que el fix es efectivo

**Tiempo total estimado**: [X] horas

---

## VALIDACIÓN POST-REMEDIACIÓN

### Prueba de Regresión

```bash
# El payload NO debe funcionar después del fix
[comando de prueba]
# Resultado esperado: [descripción del comportamiento seguro]
```

### Criterios de Cierre

- [ ] Payload de prueba bloqueado
- [ ] Tests de regresión pasando
- [ ] Sin impacto en funcionalidad existente
- [ ] Code review aprobado
- [ ] Deployed a producción

---

## REFERENCIAS

- [OWASP - Descripción del vector](https://owasp.org/www-project-top-ten/)
- [CWE-XXX](https://cwe.mitre.org/data/definitions/XXX.html)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)

---

## APROBACIÓN

**Evaluador**: [Nombre] — Fecha: ___________  
**Revisado por**: [Nombre] — Fecha: ___________  
**Aprobado por**: [Nombre] — Fecha: ___________  

---

*Confidencial - Distribución restringida*

---

**OWASP BALS v1.0.0** | Byron Antonio Lainez Sasvin  
GitHub: [@Byronsasvin](https://github.com/Byronsasvin) | Email: security@byronlainez.click
