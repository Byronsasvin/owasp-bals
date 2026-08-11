# Changelog — OWASP BALS

Todos los cambios notables de este proyecto se documentan aquí.

Formato basado en [Keep a Changelog](https://keepachangelog.com/es/1.0.0/).
Versioning basado en [Semantic Versioning](https://semver.org/lang/es/).

---

## [1.0.2] — 2026-01-XX

### Agregado
- Carpeta `templates/` con 3 plantillas listas para usar:
  - `templates/reporte-ejecutivo.md`
  - `templates/hallazgo-tecnico.md`
  - `templates/plan-remediacion.md`
- `CHANGELOG.md` para seguimiento de versiones
- GitHub Actions workflow para validación automática del power
- Soporte bilingüe (ES/EN) en `POWER.md`

### Mejorado
- `POWER.md` reescrito con sección Keywords explícita para activación automática en Kiro
- `POWER.md` incluye sección "¿Qué NO hace este Power?" para expectativas claras
- `POWER.md` incluye guía de uso por rol (Desarrollador, DevOps, CTO, Cumplimiento)
- `README.md` con inicio rápido desde el primer párrafo
- `plugin.json` con descripción expandida y keywords completos (EN + ES)
- `docs/SKILL.md` corregido — redirige al skill real en `skills/`
- `LISTA-COMPLETA-ARCHIVOS.txt` actualizada con estructura real del proyecto

### Corregido
- Referencias rotas a `./docs/EXAMPLES.md` → apuntan a `./EXAMPLES.md`
- Referencias rotas a `./templates/` → carpeta ahora existe
- `$schema` en `plugin.json` removido (apuntaba a dominio no oficial)

---

## [1.0.1] — 2026-01-XX

### Mejorado
- Descripción accesible para usuarios no expertos en seguridad
- Keywords ampliados en `plugin.json` para mejor descubrimiento

---

## [1.0.0] — 2026-01-XX

### Agregado
- Versión inicial de OWASP BALS
- OWASP Top Ten 2021 completo (10 vectores)
- Scoring CVSS v3.1 con matriz profesional
- Mapeo de cumplimiento: PCI-DSS, GDPR, HIPAA, NIST CSF, ISO 27001
- Checklist de 68 items de verificación
- 25+ payloads reales de testing
- Metodología de 5 fases
- Skill para Kiro IDE (`skills/owasp-security-testing/SKILL.md`)
- Configuración Kiro (`com.amazon.aws/kiro/kiro.json`)
- 8 ejemplos de uso completos (`EXAMPLES.md`)
- Plantillas de reporte ejecutivo y plan de remediación
- Integración con AWS Security Hub, CodeBuild y CodePipeline
- Soporte completo en español para Latinoamérica

---

[1.0.2]: https://github.com/Byronsasvin/owasp-bals/compare/v1.0.1...v1.0.2
[1.0.1]: https://github.com/Byronsasvin/owasp-bals/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/Byronsasvin/owasp-bals/releases/tag/v1.0.0
