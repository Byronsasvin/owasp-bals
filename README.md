# OWASP BALS — Marco de Pruebas de Seguridad para Kiro

Marco profesional de pruebas de seguridad web integrado en Kiro IDE. Evalúa aplicaciones contra OWASP Top Ten 2021, calcula scores CVSS v3.1, verifica cumplimiento normativo y genera reportes ejecutivos.

Diseñado para equipos de desarrollo y seguridad en Latinoamérica. Completamente en español.

---

## Inicio Rápido

Abre Kiro y escribe cualquiera de estos prompts:

```
"Realiza una evaluación de seguridad de mi aplicación"
"Evalúa este endpoint para SQL Injection"
"Genera un reporte de cumplimiento PCI-DSS"
"Calcula el score CVSS de esta vulnerabilidad"
"¿Cómo pruebo XSS en mi formulario de búsqueda?"
```

No se requiere configuración. El Power se activa automáticamente.

---

## Qué incluye

| Componente | Detalle |
|------------|---------|
| OWASP Top Ten 2021 | 10 vectores con técnicas, payloads y checklists |
| CVSS v3.1 | Scoring profesional con matriz completa |
| Cumplimiento | PCI-DSS, GDPR, HIPAA, NIST CSF, ISO 27001 |
| Checklist | 68 items de verificación exhaustiva |
| Payloads | 25+ ejemplos reales (SQL, XSS, XXE, Command Injection y más) |
| Reportes | Ejecutivos, técnicos y planes de remediación |
| AWS | Integración con Security Hub, CodeBuild, CodePipeline |

---

## Metodología de 5 Fases

1. **Reconocimiento** — Fingerprinting, enumeración de endpoints, OSINT básico
2. **Escaneo** — OWASP ZAP, Nuclei, SAST, análisis de dependencias
3. **Pruebas Manuales** — Validación de cada vector OWASP con técnicas específicas
4. **Análisis de Riesgo** — Priorización con CVSS v3.1 e impacto de negocio
5. **Reportes** — Documentación profesional con planes de remediación

---

## Instalación

### Desde la tienda de Kiro

1. Abre Kiro IDE
2. Ve a **Powers** en el panel lateral
3. Busca **OWASP BALS**
4. Haz clic en **Instalar**

### Manual

```bash
git clone https://github.com/Byronsasvin/owasp-bals.git
```

Copia la carpeta al directorio de Powers de Kiro.

---

## Ejemplos de Uso

Ver [EXAMPLES.md](./EXAMPLES.md) para 8 casos de uso completos con prompts listos para copiar.

Casos incluidos:
- Evaluación rápida pre-producción (4 horas)
- Penetration testing completo
- Auditoría de cumplimiento normativo
- Integración en pipeline DevSecOps
- Documento de hallazgo técnico
- Plan de remediación priorizado
- Reporte para Board/Inversores
- Reporte anual de seguridad

---

## Recursos

- [Documentación Técnica Completa](./skills/owasp-security-testing/SKILL.md)
- [Ejemplos de Uso](./EXAMPLES.md)
- [Guía del Power para Kiro](./POWER.md)
- [Configuración Kiro IDE](./com.amazon.aws/kiro/README.md)
- [OWASP Top Ten 2021](https://owasp.org/www-project-top-ten/)

---

## Consideraciones de Uso Ético

Este Power es una herramienta de asistencia para profesionales de seguridad. Úsalo únicamente en sistemas donde tengas autorización explícita para realizar pruebas de seguridad. El uso no autorizado en sistemas de terceros puede ser ilegal.

---

## Autor

**Byron Antonio Lainez Sasvin**

- GitHub: [@Byronsasvin](https://github.com/Byronsasvin)
- Email: security@byronlainez.click
- Instagram: [@bals.sec](https://instagram.com/bals.sec)
- Web: [byronlainez.click](https://byronlainez.click)

## Licencia

GPL-3.0-or-later — Ver [LICENSE](./LICENSE)

## Versión

1.0.0
