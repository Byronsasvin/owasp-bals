---
name: Pruebas de Seguridad OWASP
description: Metodología profesional de pruebas de seguridad OWASP Top Ten 2021 con scoring CVSS v3.1 y mapeo de cumplimiento normativo
keywords:
  - owasp
  - seguridad
  - pruebas
  - testing
  - penetración
  - vulnerabilidades
  - cvss
  - cumplimiento
  - pci-dss
  - gdpr
  - nist
  - auditoría
version: 1.0.0
---

# Pruebas de Seguridad OWASP

Metodología profesional para evaluación de seguridad en aplicaciones web usando OWASP Top Ten 2021, scoring CVSS v3.1 y mapeo de cumplimiento normativo (PCI-DSS, GDPR, HIPAA, NIST, ISO 27001).

## Descripción General

Este poder proporciona:

- **Metodología de 5 Fases**: Reconocimiento, Escaneo, Pruebas Manuales, Análisis de Riesgo, Reportes
- **OWASP Top Ten 2021 Completo**: Los 10 vectores con técnicas y payloads detallados
- **Scoring CVSS v3.1**: Evaluación profesional de vulnerabilidades con matriz completa
- **Mapeo de Cumplimiento**: PCI-DSS, GDPR, HIPAA, NIST, ISO 27001
- **Checklist de 68 Items**: Verificación exhaustiva de cada vector
- **Plantillas Profesionales**: Reutilizables para reportes, hallazgos y planes de remediación

## Casos de Uso

- Evaluaciones de seguridad y auditorías
- Pruebas de penetración (pentesting)
- Ejercicios de equipo rojo
- Validación de cumplimiento normativo (PCI-DSS, GDPR, HIPAA)
- Gestión de vulnerabilidades
- Capacitación en seguridad
- Validación post-remediación
- Reportes ejecutivos para stakeholders

## Metodología de 5 Fases

### Fase 1: Reconocimiento
Recolectar información sin explotar vulnerabilidades:
- Identificación de tecnologías
- Enumeración de endpoints y rutas
- Análisis de arquitectura de seguridad
- Recopilación de información pública
- Análisis de certificados SSL/TLS

### Fase 2: Escaneo de Vulnerabilidades
Detección automática de vulnerabilidades conocidas:
- OWASP ZAP scans
- Plantillas Nuclei
- Análisis SAST
- Escaneo de dependencias
- Testing DAST

### Fase 3: Pruebas Manuales
Validar hallazgos y probar lógica de negocio:
- Cada técnica del vector OWASP (10 vectores, 50+ pruebas)
- Validación de casos extremos
- Testing de gestión de sesión
- Intentos de bypass de autorización
- Validación de flujo lógico

### Fase 4: Análisis de Riesgo
Priorizar por impacto empresarial:
- Scoring CVSS v3.1
- Evaluación de probabilidad
- Impacto empresarial
- Contexto de cumplimiento

### Fase 5: Reportes
Documentación profesional:
- Resumen ejecutivo
- Hallazgos técnicos detallados
- Planes de remediación
- Criterios de validación
- Cronograma

## OWASP Top Ten 2021 - Referencia Rápida

| ID | Vector | CVSS | Técnicas Clave |
|----|--------|------|-----------------|
| A01 | Inyección | 9.8 | SQL, NoSQL, Comandos, LDAP |
| A02 | Autenticación Rota | 9.3 | Fuerza bruta, Sesiones, Credenciales |
| A03 | Exposición de Datos | 7.5 | Encriptación, PII, Transmisión |
| A04 | Control de Acceso Roto | 9.1 | IDOR, Escalación, Autorización |
| A05 | Configuración Incorrecta | 8.6 | Headers, Debug, Defaults |
| A06 | XXE | 9.8 | XML, Entidad Externa, OOB |
| A07 | Autenticación API Rota | 9.1 | JWT, Claves, OAuth, Rate Limiting |
| A08 | XSS | 7.1 | Reflejado, Almacenado, DOM |
| A09 | Deserialización Insegura | 9.8 | Java, Python, PHP, RCE |
| A10 | Logging y Monitoreo | 7.5 | Logs, Alertas, SIEM, Retención |

## Scoring CVSS v3.1

### Matriz Rápida

| Rango | Severidad |
|-------|-----------|
| 9.0-10.0 | CRÍTICA |
| 7.0-8.9 | ALTA |
| 4.0-6.9 | MEDIA |
| 0.1-3.9 | BAJA |

### Formato de Vector

`CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H = 9.8`

### Métricas Clave

- **AV** (Vector de Ataque): Red, Adyacente, Local, Físico
- **AC** (Complejidad): Baja, Alta
- **PR** (Privilegios): Ninguno, Bajo, Alto
- **UI** (Interacción Usuario): Ninguna, Requerida
- **S** (Alcance): Sin cambios, Cambiado
- **C/I/A** (Impacto): Ninguno, Bajo, Alto

## Ejemplos de Payloads

### Inyección SQL
```sql
' OR '1'='1' --
' UNION SELECT * FROM usuarios --
' ; DROP TABLE usuarios; --
```

### XSS
```html
<script>alert('XSS')</script>
<img src=x onerror="alert('XSS')">
<svg onload="alert('XSS')">
```

### Inyección de Comandos
```bash
; whoami
| cat /etc/passwd
` id `
```

## Mapeo de Cumplimiento Normativo

Cada hallazgo se mapea a:
- **PCI-DSS v3.2.1**: Protección de datos de tarjetahabientes
- **GDPR**: Protección de datos personales
- **HIPAA**: Protección de datos de salud
- **NIST CSF**: Mejores prácticas de ciberseguridad
- **ISO 27001**: Seguridad de la información

## Checklist de Pruebas

- Reconocimiento: 5 items
- Escaneo: 5 items
- Pruebas Manuales: 50+ items (10 por vector)
- Análisis de Riesgo: 4 items
- Reportes: 4 items

**Total**: 68+ items de verificación

## Prompts para Usar Este Poder

### Evaluación Completa de Seguridad
```
Realiza una evaluación completa de seguridad de [URL] usando OWASP BALS.
Incluye los 10 vectores, scoring CVSS, mapeo de cumplimiento (PCI-DSS, GDPR),
y un plan de remediación con cronograma.
```

### Testing de Vector Específico
```
Prueba este endpoint para vulnerabilidades de A01 Inyección usando OWASP BALS.
Proporciona payloads, pasos de validación, score CVSS, impacto empresarial,
y ejemplos de código de remediación (SQL, Python, Node.js).
```

### Reporte Ejecutivo
```
Genera un reporte de seguridad ejecutivo para [aplicación] usando OWASP BALS.
Incluye matriz de riesgo, resumen de hallazgos, brechas de cumplimiento (PCI-DSS, GDPR),
y plan de acción priorizado.
```

### Validación Post-Remediación
```
Valida que esta vulnerabilidad [descripción] ha sido remediada correctamente
usando la metodología OWASP BALS. Proporciona pasos de testing y criterios de éxito.
```

## Características Clave

✓ **Integral**: Los 10 vectores OWASP con 6-10 subtécnicas cada uno
✓ **Práctica**: 25+ payloads reales y técnicas de testing
✓ **Estandarizada**: Scoring CVSS v3.1 con matriz profesional
✓ **Normativa**: Mapeo PCI-DSS, GDPR, HIPAA, NIST, ISO 27001
✓ **Profesional**: Resúmenes ejecutivos, detalles técnicos, planes de remediación
✓ **Verificada**: Checklist de 68 items para completitud

## Entregas

**1. Reporte Ejecutivo**
- Resumen de hallazgos
- Matriz de riesgo
- Brechas de cumplimiento
- Plan de acción

**2. Hallazgos Técnicos**
- Descripción por vulnerabilidad
- Pasos de reproducción
- Score CVSS
- Impacto empresarial
- Ejemplos de código de remediación

**3. Plan de Remediación**
- Enfoque por fases
- Asignación de recursos
- Cronograma
- Métricas de éxito
- Criterios de cierre

## Estándares y Referencias

- [OWASP Top Ten 2021](https://owasp.org/www-project-top-ten/)
- [CVSS v3.1 Specification](https://www.first.org/cvss/v3.1/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [CWE - Common Weakness Enumeration](https://cwe.mitre.org/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)

## Historial de Versiones

- **v1.0.0** (Enero 2026): Versión inicial con OWASP Top Ten 2021, CVSS v3.1, mapeo de cumplimiento

## Autor

Byron Antonio Lainez Sasvin
- GitHub: [@Byronsasvin](https://github.com/Byronsasvin)
- Instagram: [@bals.sec](https://instagram.com/bals.sec)
- Email: security@byronlainez.click
- Sitio Web: [byronlainez.click](https://byronlainez.click)

---

**Para detalles técnicos completos, metodología, payloads y checklists, ver la documentación en el repositorio del poder.**
