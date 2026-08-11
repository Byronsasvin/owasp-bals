<<<<<<< HEAD
# OWASP BALS - Kiro IDE Power

**OWASP BALS as a Kiro IDE Security Power for AWS**

This is the Kiro IDE specific configuration and documentation for using OWASP BALS as a professional security testing power within AWS Kiro IDE.

## Quick Start

### 1. Install in Kiro IDE

```bash
# In Kiro IDE terminal or command palette
kiro install owasp-bals
```

### 2. Access the Power

- Open Kiro IDE
- Go to **Customize** → **Powers**
- Select **OWASP BALS - Security Testing Power**
- Add to your workspace

### 3. Use in Chat

Reference the power directly in your queries:

```
"@owasp-bals perform a security assessment of my web application"
"@owasp-bals test for A01 Injection vulnerabilities"
"@owasp-bals generate a PCI-DSS compliance report"
```

## Features in Kiro IDE

### Quick Actions

| Action | Command | Description |
|--------|---------|-------------|
| Quick Assessment | `Quick Security Assessment` | Fast OWASP evaluation |
| Full Analysis | `OWASP Top 10 Analysis` | Complete 10-vector testing |
| Compliance | `Compliance Report` | PCI-DSS, GDPR, HIPAA validation |
| CVSS Scoring | `Vulnerability Scoring` | Professional CVSS v3.1 scoring |

### Pre-Built Prompts

Available in Kiro IDE's AI prompt library:

1. **Security Assessment**
   - Complete OWASP evaluation
   - All 10 vectors tested
   - CVSS scoring included

2. **Specific Vector Testing**
   - Target single OWASP vector
   - Detailed techniques and payloads
   - Remediation guidance

3. **Executive Report**
   - C-level summary
   - Risk matrix
   - Compliance mapping
   - Action plan

4. **CI/CD Integration**
   - AWS CodeBuild setup
   - CodePipeline integration
   - Automated scanning

## AWS Integration

### Security Hub

Automatically publish findings to AWS Security Hub:

```json
{
  "AwsAccountId": "123456789012",
  "Region": "us-east-1",
  "Types": ["Software and Configuration Checks/OWASP"],
  "Severity": {"Label": "CRITICAL"},
  "Resources": [
    {
      "Type": "AwsApiCall",
      "Id": "security-assessment"
    }
  ]
}
```

### EventBridge

Trigger automated responses:

```bash
# Publish OWASP findings to EventBridge
# Automatically trigger remediation workflows
# Send SNS notifications
```

### CodePipeline Integration

Add security scanning to your CI/CD:

```yaml
SecurityStage:
  - Action: RunOWASPBals
    Provider: OWASP-BALS
    Input:
      - Repository
      - Branch
    Output:
      - SecurityReport
      - Findings
```

## Usage Examples

### Example 1: Quick Web App Security Check

```
User: "@owasp-bals I have a Node.js web application at example.com. 
What are the critical security issues?"

OWASP BALS Response:
- Full OWASP Top Ten assessment
- CVSS scores for each finding
- Quick remediation steps
- PCI-DSS compliance gaps
```

### Example 2: Compliance Validation

```
User: "@owasp-bals Our application must be PCI-DSS compliant. 
Generate a compliance report."

OWASP BALS Response:
- PCI-DSS requirement mapping
- Current compliance status
- Gap analysis
- Remediation roadmap
- Timeline
```

### Example 3: Post-Remediation Validation

```
User: "@owasp-bals We fixed SQL injection vulnerabilities. 
Validate the remediation."

OWASP BALS Response:
- Testing methodology
- Validation steps
- Success criteria
- Pass/fail results
- Sign-off checklist
```

### Example 4: CI/CD Security Pipeline

```
User: "@owasp-bals Set up automated security scanning in our 
AWS CodePipeline"

OWASP BALS Response:
- CodeBuild project configuration
- OWASP BALS scanning steps
- Security Hub integration
- Notification setup
- Policy enforcement
```

## Command Reference

### Assessment Commands

```bash
# Quick security assessment
owasp-bals:quick-assessment --app-url <URL>

# Full OWASP Top 10 analysis
owasp-bals:full-analysis --app-url <URL> --depth complete

# Specific vector testing
owasp-bals:vector-test --vector A01 --app-url <URL>

# Compliance report
owasp-bals:compliance-report --frameworks PCI-DSS,GDPR --app-url <URL>

# CVSS scoring
owasp-bals:cvss-score --vulnerability "<description>"

# Generate report
owasp-bals:report --format executive --output s3://bucket/
```

### Integration Commands

```bash
# Publish to Security Hub
owasp-bals:publish-hub --region us-east-1 --account 123456789012

# Send EventBridge event
owasp-bals:publish-event --detail-type "OWASP Finding"

# Setup CodePipeline
owasp-bals:setup-pipeline --repository my-app --branch main

# Configure SNS notifications
owasp-bals:setup-notifications --topic arn:aws:sns:...
```

## Kiro IDE Integration Details

### Installation

In Kiro IDE:
1. Go to **Customize** tab
2. Click **Powers**
3. Search "OWASP BALS"
4. Click **Install**
5. Authorize AWS permissions (if using integrations)

### Authorization

The power can optionally access:
- **AWS Security Hub** (read/write findings)
- **AWS CodeBuild** (read build logs)
- **AWS CodePipeline** (read pipeline status)
- **AWS SNS** (send notifications)
- **AWS S3** (store reports)

These are optional and only needed for AWS integration features.

### Prompt Templates

Available directly in Kiro IDE's prompt library:

- **@owasp-bals Security Assessment**
- **@owasp-bals Vulnerability Analysis**
- **@owasp-bals Compliance Check**
- **@owasp-bals CI/CD Setup**

## Configuration

### User Preferences (in Kiro IDE Settings)

```json
{
  "owasp-bals": {
    "defaultTemplate": "executive",
    "autoScoring": true,
    "complianceFrameworks": ["PCI-DSS", "GDPR"],
    "awsIntegration": {
      "securityHub": true,
      "region": "us-east-1"
    },
    "reportFormat": "markdown"
  }
}
```

## Advanced Features

### Custom Payloads

Define custom testing payloads in Kiro settings:

```json
{
  "customPayloads": [
    {
      "vector": "A01",
      "payload": "' OR '1'='1' --",
      "name": "SQLi Basic"
    }
  ]
}
```

### Integration with Copilot

The power can assist GitHub Copilot in VS Code:

```bash
# In VS Code with Copilot extension
# Use @owasp-bals in chat for security guidance
```

### Multi-Cloud Support

While optimized for AWS, the power works with:
- Azure (via integrations)
- GCP (via integrations)
- On-premise applications

## Support & Documentation

- **Repository**: https://github.com/Byronsasvin/owasp-bals
- **Issues**: https://github.com/Byronsasvin/owasp-bals/issues
- **Discussions**: https://github.com/Byronsasvin/owasp-bals/discussions
- **Email**: security@byronlainez.click

## Kiro IDE Version Support

- **Minimum Kiro IDE Version**: 1.0.0
- **Tested with**: Kiro IDE 1.0.0+
- **Status**: Production Ready

## License

GNU General Public License v3.0 or later (GPL-3.0-or-later)

## Author

**Byron Antonio Lainez Sasvin**
- GitHub: [@Byronsasvin](https://github.com/Byronsasvin)
- Instagram: [@bals.sec](https://instagram.com/bals.sec)
- Email: security@byronlainez.click
- Website: [byronlainez.click](https://byronlainez.click)

---

## Kiro IDE Roadmap

Planned features for future versions:

- Real-time scanning in Kiro IDE editor
- Integrated remediation suggestions
- Custom vulnerability templates
- Multi-project assessment
- Team collaboration features
- Advanced reporting dashboard

---

**Ready to secure your AWS applications with OWASP BALS in Kiro IDE!**
=======
# OWASP BALS - Security Testing Framework

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL3.0-blue.svg)](https://github.com/bals-sec/owasp-bals/blob/main/LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.0-green.svg)](https://github.com/bals-sec/owasp-bals/releases/tag/v1.0.0)
[![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen.svg)](.)
[![Agent Plugins](https://img.shields.io/badge/Agent%20Plugins-1.0.0-orange.svg)](https://agent-plugins.org)

Framework profesional de evaluación de seguridad para aplicaciones web basado en **OWASP Top Ten 2021**.

Desarrollado por **Byron Antonio Lainez Sasvin** ([@bals.sec](https://x.com/bals.sec))

---

## Características Principales

### Cobertura OWASP Top Ten 2021

| Vector | CVSS | Status |
|--------|------|--------|
| A01:2021 - Injection | 9.8 | ✓ Completo |
| A02:2021 - Broken Authentication | 9.3 | ✓ Completo |
| A03:2021 - Sensitive Data Exposure | 7.5 | ✓ Completo |
| A04:2021 - Broken Access Control | 9.1 | ✓ Completo |
| A05:2021 - Security Misconfiguration | 8.6 | ✓ Completo |
| A06:2021 - XXE | 9.8 | ✓ Completo |
| A07:2021 - Broken Authentication (API) | 9.1 | ✓ Completo |
| A08:2021 - XSS | 7.1 | ✓ Completo |
| A09:2021 - Insecure Deserialization | 9.8 | ✓ Completo |
| A10:2021 - Insufficient Logging | 7.5 | ✓ Completo |

### Entregables Profesionales

- **Reportes Ejecutivos** - 1-2 páginas, resumen C-level
- **Documentación Técnica** - Hallazgos detallados con evidence
- **Planes de Remediación** - Priorización por riesgo y timeline
- **Scoring CVSS v3.1** - Vector strings completos con severidad
- **Mapeo de Compliance** - PCI-DSS, GDPR, NIST, ISO 27001

### Compatibilidad Multi-Plataforma

```
Claude.ai          ✓ Funciona ahora
Kiro (AWS)         ✓ Agent Plugin ready
Cursor             ✓ Compatible
GitHub Copilot     ✓ Compatible
OpenAI Copilot CLI ✓ Compatible
```

---

## Inicio Rápido

### Instalación

#### En Claude.ai

```bash
# Settings → Skills → Upload folder
# Seleccionar carpeta owasp-bals/
```

#### En Kiro

```bash
kiro plugin install owasp-bals
```

#### En Cursor

```bash
# Command Palette → Agent Extensions
# Buscar: OWASP BALS
# Clic: Install
```

### Uso Básico

```markdown
Realiza evaluación OWASP Top Ten de https://myapp.com

Scope:
- Endpoints: /login, /api/profile, /api/payments
- Usuarios de prueba disponibles

Entrega:
1. Hallazgos por vector OWASP
2. CVSS score por hallazgo
3. Reporte ejecutivo (1 página)
4. Plan de remediación priorizado

Formato: Markdown listo para compartir con CTO
```

---

## Casos de Uso

### 1. Evaluación Pre-Producción (4-8 horas)

```
Análisis rápido de aplicación antes de lanzamiento
└─ Entrega: Reporte ejecutivo + hallazgos críticos
```

### 2. Penetration Testing Completo (1-2 semanas)

```
Testing manual y automatizado de todos los vectores
└─ Entrega: Reporte técnico 50+ páginas + Jira tickets
```

### 3. Auditoría de Compliance (1 semana)

```
Evaluación contra PCI-DSS, GDPR, NIST, ISO 27001
└─ Entrega: Matriz de mapping + evidence documentada
```

### 4. DevSecOps Pipeline

```
Integración en CI/CD para escaneos automatizados
└─ Entrega: Notificaciones automáticas de hallazgos
```

---

## Estructura del Proyecto

```
owasp-bals/
├── README.md                              # Este archivo
├── plugin.json                            # Manifest Agent Plugins
├── LICENSE                                # GPL-3.0-or-later
├── .gitignore                             # Git configuration
├── CHANGELOG.md                           # Historial de cambios
├── SECURITY.md                            # Política de seguridad
├── CONTRIBUTING.md                        # Guía de contribución
│
├── .github/
│   ├── workflows/
│   │   ├── validate.yml                  # CI: Validación de código
│   │   ├── test.yml                      # CI: Testing
│   │   └── publish.yml                   # CD: Publicación
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
│
├── docs/
│   ├── SKILL.md                          # Metodología OWASP completa
│   ├── INTEGRATION.md                    # Setup en todas plataformas
│   ├── EXAMPLES.md                       # 8 casos de uso con prompts
│   ├── API.md                            # Referencia de API
│   └── FAQ.md                            # Preguntas frecuentes
│
├── skills/owasp-bals/
│   ├── SKILL.md                          # Definición de la skill
│   ├── references/
│   │   ├── owasp-top-ten-2021.json      # Base de datos de vectores
│   │   ├── cvss-base-scores.json        # Scores de CVSS
│   │   └── compliance-mapping.json      # Mapeo PCI/GDPR/NIST
│   └── scripts/
│       └── generate-report.js            # Generador de reportes
│
├── templates/
│   ├── reporte-ejecutivo.md             # Template C-level
│   ├── hallazgo-tecnico.md              # Template técnico
│   ├── plan-remediacion.md              # Template remediation
│   └── matriz-compliance.md             # Template compliance
│
├── scripts/
│   ├── publish.sh                        # Publicación automática
│   ├── validate.sh                       # Validación de archivos
│   └── setup.sh                          # Setup inicial
│
└── tests/
    ├── unit/
    └── integration/
```

---

## Documentación

| Documento | Contenido | Tiempo |
|-----------|-----------|--------|
| [**SKILL.md**](docs/SKILL.md) | Metodología OWASP, 10 vectores, payloads ejemplo | 30 min |
| [**EXAMPLES.md**](docs/EXAMPLES.md) | 8 casos de uso reales con prompts listos | 20 min |
| [**INTEGRATION.md**](docs/INTEGRATION.md) | Setup en Kiro, Cursor, Copilot, Claude | 15 min |
| [**API.md**](docs/API.md) | Referencia completa de funciones | 25 min |
| [**FAQ.md**](docs/FAQ.md) | Preguntas frecuentes y troubleshooting | 10 min |

---

## Ejemplos de Uso

### Prompt 1: Evaluación Rápida

```markdown
Realiza evaluación OWASP Top Ten de https://myapp.com

Scope:
- Endpoints principales
- Funcionalidad de login
- APIs de pago

Entrega:
1. Hallazgos por vector OWASP
2. CVSS score por hallazgo
3. Reporte ejecutivo (1 página)
4. Plan de remediación priorizado
```

### Prompt 2: Documentar Hallazgo

```markdown
Documenta hallazgo de seguridad OWASP #1 (Injection):

Donde: POST /api/search
Parámetro: q=
Payload: ' OR '1'='1
Respuesta: [muestro output]

Incluye:
- Reproducción paso a paso
- Vector CVSS completo
- Impacto en negocio
- Código de remediación en Python/Java/Node
```

### Prompt 3: Reporte Profesional

```markdown
Genera reporte ejecutivo de evaluación OWASP.

Hallazgos encontrados:
- SQLi (CVSS 9.8) x2
- Auth Bypass (CVSS 9.1) x1
- XSS (CVSS 7.1) x3

Audiencia: CEO/CFO
Incluir: Business impact, timeline, recursos
Formato: Markdown para compartir
```

---

## Output de Ejemplo

### Reporte Ejecutivo Generado

```markdown
# EVALUACIÓN OWASP TOP TEN - MyApp Staging

Fecha: 15/01/2026 | Evaluador: OWASP BALS | Tiempo: 4 horas

## Resumen Ejecutivo

La aplicación presenta **2 vulnerabilidades críticas** que deben remediarse 
ANTES de producción.

**Recomendación**: Proceder a producción DESPUÉS de remediación.

## Hallazgos por Severidad

| Severidad | Cantidad | Timeline | Equipo |
|-----------|----------|----------|--------|
| Crítica | 2 | 24h | Backend |
| Alta | 3 | 1 semana | Full-stack |
| Media | 2 | 2 semanas | Backend |
| Baja | 0 | - | - |

## Hallazgos Críticos

### 1. SQL Injection en /api/search (CVSS 9.8)
Riesgo: Acceso total a datos | Timeline: 6h | Equipo: Backend

### 2. Session Fixation (CVSS 9.1)
Riesgo: Account takeover | Timeline: 4h | Equipo: Backend

## Conclusión

Aplicación lista para producción en **24 horas**.
```

---

## Características Técnicas

### Scoring CVSS v3.1

Cada hallazgo incluye:
- Vector string completo: `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H`
- Score numérico: 9.8 CRITICAL
- Severidad: CRITICAL, HIGH, MEDIUM, LOW

### Mappeo de Compliance

Cada hallazgo se mapea a:
- **PCI-DSS**: Requisitos específicos (6.5.1, 6.5.7, etc)
- **GDPR**: Artículos relevantes (32, 33, etc)
- **NIST**: Familias de controles (SI-2, IA-5, etc)
- **ISO 27001**: Controles (A.6.2.1, A.12.2.1, etc)

### MCP Server Incluido

Compatible con Kiro y otros agentes que soportan MCP:

```bash
# Automático en Kiro
# Manual para otros:
mcp run owasp-bals-server
```

---

## Instalación para Desarrollo

```bash
# Clonar repositorio
git clone https://github.com/bals-sec/owasp-bals.git
cd owasp-bals

# Setup inicial
./scripts/setup.sh

# Validar configuración
./scripts/validate.sh

# Ejecutar tests
npm test
```

---

## Contribuir

Las contribuciones son bienvenidas. Ver [CONTRIBUTING.md](CONTRIBUTING.md) para detalles.

```bash
1. Fork el repositorio
2. Crea una rama (git checkout -b feature/amazing)
3. Commit cambios (git commit -m 'Add amazing feature')
4. Push rama (git push origin feature/amazing)
5. Abre Pull Request
```

---

## Reportar Vulnerabilidades

Para reportar vulnerabilidades de seguridad, contactar privadamente:

**Email**: security@byronlainez.click  
**GPG Key**: [Available on keybase.io/bals_sec](https://keybase.io/bals_sec)

Ver [SECURITY.md](SECURITY.md) para detalles.

---

## Licencia

GPL-3.0-or-later

Este software está disponible bajo licencia GPL-3.0. Ver [LICENSE](LICENSE) para términos completos.

---

## Roadmap

### v1.0.0 (Actual)
- ✓ 10 vectores OWASP Top Ten
- ✓ CVSS v3.1 scoring
- ✓ Reportes ejecutivos
- ✓ Templates profesionales

### v1.1.0 (Q2 2026)
- GraphQL API testing
- Mobile app testing vectors
- Automated scanning integrations

### v2.0.0 (Q4 2026)
- OWASP Top Ten 2024/2025
- Supply chain scanning (SBOM)
- Dashboard y compliance tracking

---

## Créditos

Desarrollado por **Byron Antonio Lainez Sasvin**

- GitHub: [@bals-sec](https://github.com/bals-sec)
- Twitter/X: [@bals.sec](https://x.com/bals.sec)
- Email: security@byronlainez.click
- Website: [byronlainez.click](https://byronlainez.click)

### Inspiración

- OWASP Foundation
- CWE/CAPEC/CVSS standards
- Metodología de pentesting profesional

---

## Soporte

| Canal | Link |
|-------|------|
| **Issues** | [GitHub Issues](https://github.com/bals-sec/owasp-bals/issues) |
| **Discussions** | [GitHub Discussions](https://github.com/bals-sec/owasp-bals/discussions) |
| **Email** | security@byronlainez.click |
| **Website** | [byronlainez.click](https://byronlainez.click) |

---

## Star History

Si este proyecto te resulta útil, considera darle una estrella en GitHub.

---

**OWASP BALS v1.0.0**  
Enero 2026 | Producción Ready  
[GitHub](https://github.com/bals-sec/owasp-bals) | [License](LICENSE)
>>>>>>> 4a7314d329c05909a64e75938bc439c715ed308a
