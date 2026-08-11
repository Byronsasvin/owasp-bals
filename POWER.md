# OWASP BALS - Security Testing Power

**Keywords**: owasp, seguridad, security, pruebas, testing, penetración, pentest, vulnerabilidades, vulnerabilities, cvss, cumplimiento, compliance, pci-dss, gdpr, hipaa, nist, iso27001, evaluación, auditoría, inyección, injection, xss, autenticación

---

## ¿Qué es este Power?

OWASP BALS es un marco profesional de pruebas de seguridad para aplicaciones web, integrado directamente en Kiro. Te permite realizar evaluaciones de seguridad completas siguiendo la metodología OWASP Top Ten 2021, calcular scores CVSS v3.1, verificar cumplimiento normativo y generar reportes ejecutivos, sin salir del IDE.

Diseñado para equipos de desarrollo, seguridad y cumplimiento en Latinoamérica, con soporte completo en español.

---

## ¿Qué puedes hacer con este Power?

| Capacidad | Descripción |
|-----------|-------------|
| **Evaluación OWASP Top Ten** | Analiza los 10 vectores de ataque más críticos de 2021 |
| **Scoring CVSS v3.1** | Calcula la severidad de vulnerabilidades con estándar internacional |
| **Mapeo de Cumplimiento** | Verifica requisitos de PCI-DSS, GDPR, HIPAA, NIST e ISO 27001 |
| **Checklist de 68 items** | Guía de verificación exhaustiva por vector OWASP |
| **25+ Payloads reales** | Ejemplos listos para testing de SQL Injection, XSS, XXE y más |
| **Reportes Profesionales** | Genera reportes ejecutivos, técnicos y planes de remediación |
| **Integración AWS** | Conecta con Security Hub, CodeBuild y CodePipeline |

---

## Cómo activar este Power

Este Power se activa automáticamente cuando mencionas cualquiera de estos términos en Kiro:

```
seguridad, security, owasp, pruebas, testing, pentest, penetración,
vulnerabilidades, cvss, compliance, cumplimiento, pci-dss, gdpr,
evaluación, auditoría, inyección, xss, autenticación
```

No necesitas configuración adicional. Solo escribe tu solicitud en lenguaje natural.

---

## Guía de Uso Rápido

### Para alguien que nunca usó OWASP

Si nunca has hecho una evaluación de seguridad, empieza con este prompt:

```
Necesito evaluar la seguridad de mi aplicación web [URL o descripción].
¿Por dónde empiezo? Guíame paso a paso.
```

Kiro te explicará el proceso y adaptará la evaluación a tu nivel.

---

### Prompts listos para usar

**1. Evaluación completa (punto de partida recomendado)**
```
Realiza una evaluación completa de seguridad de [URL o nombre de app]
usando OWASP BALS. Incluye los 10 vectores, scoring CVSS, mapeo de
cumplimiento PCI-DSS y GDPR, y un plan de remediación con cronograma.
```

**2. Analizar un vector específico**
```
Evalúa [URL o endpoint] para vulnerabilidades de [nombre del vector].
Por ejemplo: SQL Injection (A01), Control de Acceso Roto (A04), XSS (A08).
Incluye payloads de prueba, score CVSS y código de remediación.
```

**3. Generar reporte ejecutivo**
```
Genera un reporte ejecutivo de seguridad para [nombre de la aplicación].
Audiencia: [CTO / Board / Inversores]. Incluye matriz de riesgo,
hallazgos principales, brechas de cumplimiento y plan de acción.
```

**4. Validar una remediación**
```
Verifica que la vulnerabilidad [descripción] en [endpoint] ha sido
corregida. Proporciona los pasos de validación y criterios de éxito.
```

**5. Preparar auditoría de cumplimiento**
```
Evalúa [aplicación] contra los requisitos de [PCI-DSS / GDPR / HIPAA].
Genera matriz de cumplimiento con gaps identificados y roadmap de remediación.
```

---

## Metodología de 5 Fases

Este Power sigue un proceso estructurado:

```
Fase 1: Reconocimiento   → Identificar tecnologías y superficie de ataque
Fase 2: Escaneo          → Detección automática de vulnerabilidades conocidas
Fase 3: Pruebas Manuales → Validar hallazgos y explorar lógica de negocio
Fase 4: Análisis de Riesgo → Priorizar por impacto con CVSS v3.1
Fase 5: Reportes         → Documentación profesional de hallazgos
```

---

## OWASP Top Ten 2021 — Referencia Rápida

| ID | Vector | Severidad | Ejemplo de Ataque |
|----|--------|-----------|-------------------|
| A01 | Inyección | CRÍTICA (9.8) | SQL Injection, Command Injection |
| A02 | Autenticación Rota | ALTA (9.3) | Fuerza bruta, sesiones débiles |
| A03 | Exposición de Datos | ALTA (7.5) | Datos sin cifrar, claves expuestas |
| A04 | Control de Acceso Roto | CRÍTICA (9.1) | IDOR, escalada de privilegios |
| A05 | Configuración Incorrecta | ALTA (8.6) | Headers faltantes, debug en prod |
| A06 | XXE | CRÍTICA (9.8) | Lectura de archivos del servidor |
| A07 | Autenticación API Rota | CRÍTICA (9.1) | JWT inválido, sin rate limiting |
| A08 | XSS | ALTA (7.1) | JavaScript inyectado en navegador |
| A09 | Deserialización Insegura | CRÍTICA (9.8) | Ejecución remota de código (RCE) |
| A10 | Logging y Monitoreo | ALTA (7.5) | Sin alertas en eventos críticos |

---

## ¿Qué NO hace este Power?

- No ejecuta ataques reales contra sistemas en producción
- No reemplaza una prueba de penetración manual por un profesional certificado
- No garantiza el 100% de cobertura de vulnerabilidades
- No accede directamente a tu infraestructura (solo guía el proceso)

**Importante**: Usa este Power únicamente en sistemas que tienes autorización para evaluar.

---

## Casos de Uso por Rol

**Desarrollador**
> "Quiero revisar si mi nuevo endpoint tiene vulnerabilidades antes de hacer el PR"

**Equipo de seguridad**
> "Necesito una evaluación OWASP completa con evidencia para el reporte de auditoría"

**DevOps / DevSecOps**
> "Quiero integrar escaneos automáticos en el pipeline de CI/CD con AWS CodeBuild"

**CTO / Manager**
> "Necesito un reporte ejecutivo de riesgos de seguridad para presentar al board"

**Equipo de cumplimiento**
> "Debo demostrar cumplimiento PCI-DSS antes de la certificación"

---

## Recursos

- [Skill técnica detallada](../../skills/owasp-security-testing/SKILL.md)
- [Ejemplos prácticos con prompts completos](../../EXAMPLES.md)
- [Configuración para Kiro IDE](../../com.amazon.aws/kiro/README.md)
- [OWASP Top Ten 2021](https://owasp.org/www-project-top-ten/)
- [Calculadora CVSS v3.1](https://www.first.org/cvss/calculator/3.1)

---

## Autor

**Byron Antonio Lainez Sasvin**  
Security Researcher · LATAM

- GitHub: [@Byronsasvin](https://github.com/Byronsasvin)
- Email: security@byronlainez.click
- Instagram: [@bals.sec](https://instagram.com/bals.sec)
- Web: [byronlainez.click](https://byronlainez.click)

**Licencia**: GPL-3.0-or-later  
**Versión**: 1.0.0
