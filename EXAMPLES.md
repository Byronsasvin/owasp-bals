# Ejemplos de Uso - OWASP BALS

8 casos de uso reales con prompts listos para copiar y pegar.

## Ejemplo 1: Evaluación Rápida Pre-Producción

```markdown
Realiza evaluación OWASP Top Ten rápida de https://staging.myapp.com

Scope:
- Endpoints críticos: /api/login, /api/profile, /api/payments
- Usuarios de prueba disponibles
- Tiempo disponible: 4 horas

Entrega:
1. Hallazgos críticos y altos solo
2. Reporte ejecutivo (máx 2 páginas)
3. Plan de remediación de 1 página
4. Veredicto: Proceder a Prod / Bloquear

Formato: Markdown listo para CTO
```

**Tiempo**: 4-8 horas  
**Entrega**: Reporte ejecutivo + hallazgos críticos

---

## Ejemplo 2: Penetrating Testing Completo

```markdown
Realiza evaluación completa de OWASP Top Ten en https://myapp.com

Scope completo:
- Todos los endpoints
- Autenticación y autorización
- Manejo de datos
- APIs internas y externas

Metodología:
1. Reconnaissance completo
2. Manual testing de cada vector
3. Automated scanning
4. Risk assessment CVSS

Documentación:
- Hallazgo técnico por cada vector (con payload, evidence, impacto)
- CVSS v3.1 scores completos
- Código de remediación en [lenguaje]
- Screenshots/evidence de cada issue

Entrega final:
- Reporte técnico profesional (50+ páginas)
- Executive summary
- Jira tickets listos para desarrollo
- Remediation roadmap
```

**Tiempo**: 1-2 semanas  
**Entrega**: Reporte completo + tickets + roadmap

---

## Ejemplo 3: Compliance Auditoría

```markdown
Evalúa cumplimiento de OWASP Top Ten contra requisitos de compliance

Estándares a verificar:
- PCI-DSS (si maneja tarjetas)
- GDPR (si tiene datos de EU)
- NIST (si es federal/gobierno)
- ISO 27001 (si lo requiere)

Por cada hallazgo OWASP:
1. Vector de OWASP
2. Requisito de compliance que viola
3. Evidence técnica
4. Impacto de compliance
5. Timeline de remediación
6. Recursos requeridos

Entrega:
- Matriz OWASP ↔ Compliance
- Reporte de gaps
- Evidence documentada
- Roadmap de remediación
```

**Tiempo**: 1 semana  
**Entrega**: Matriz de mapping + evidence + roadmap

---

## Ejemplo 4: DevSecOps Pipeline Integration

```markdown
Configura OWASP BALS en pipeline CI/CD

Integración:
- Escaneos automáticos en staging post-deploy
- Notificaciones de hallazgos críticos
- Bloquear deploy si hay críticos
- Reportes automáticos a dashboard

Configuración:
- Frecuencia: Cada deploy
- Timeout: 30 minutos
- Notificaciones: Slack, Email, Jira
- Escalation: Critical → en 24h

Métricas:
- Total de hallazgos por build
- Trend de vulnerabilidades
- MTTR (Mean Time To Remediate)
- Vulnerabilidades resueltas
```

**Tiempo**: Configuración inicial 4h  
**Benefit**: Detección continua

---

## Ejemplo 5: Documento Hallazgo Técnico Específico

```markdown
Documenta hallazgo de OWASP #1 (Injection):

Información técnica:
- Endpoint: POST /api/search
- Parámetro: q=
- Tipo: SQL Injection
- Severidad: CVSS 9.8 CRITICAL
- CWE: CWE-89
- CAPEC: CAPEC-66

Payload de prueba:
' OR '1'='1
' UNION SELECT * FROM users --
' ; DROP TABLE users; --

Response observada:
[Pega aquí el output del servidor]

Impacto:
- Acceso no autorizado a datos
- Posible eliminación de datos
- Exposición de PII
- Violación de GDPR/PCI-DSS

Remediación - Código Python:
# Antes (Vulnerable)
query = f"SELECT * FROM users WHERE email = '{email}'"
result = db.execute(query)

# Después (Seguro)
query = "SELECT * FROM users WHERE email = ?"
result = db.execute(query, (email,))

Remediación - Código Node.js:
// Antes (Vulnerable)
const query = `SELECT * FROM users WHERE email = '${email}'`;
db.query(query);

// Después (Seguro)
const query = "SELECT * FROM users WHERE email = ?";
db.query(query, [email]);

Validación post-remediación:
1. Fuzzing con payloads OWASP
2. SAST scanning
3. Manual verification
4. Re-testing antes de producción
```

**Tiempo**: 2-4 horas por hallazgo  
**Entrega**: Documentación técnica profesional

---

## Ejemplo 6: Plan de Remediación Priorizado

```markdown
Crea plan de remediación para hallazgos encontrados

Hallazgos a remediar:
- SQLi (CVSS 9.8) - 2 instancias
- Auth Bypass (CVSS 9.1) - 1 instancia
- XSS (CVSS 7.1) - 3 instancias
- Misc Config (CVSS 6.5) - 2 instancias

Formato entrega:
1. Matriz de riesgo/urgencia
2. Timeline por fase (Analysis → Implementation → Testing → Validation)
3. Equipo responsable por issue
4. Dependencias entre issues
5. Recursos requeridos (personas-hora, herramientas)
6. KPIs de éxito
7. Rollback plan si falla

Phases:
- Phase 1 (Semana 1): Críticos - SQLi + Auth
- Phase 2 (Semana 2): Altos - XSS
- Phase 3 (Semana 3): Medios - Misc Config

Métricas:
- Semana 1: Reducir de 7 críticos a 0
- Semana 2: Reducir altos 50%
- Semana 3: Completar remediación
```

**Tiempo**: 4 horas de planning  
**Entrega**: Roadmap ejecutable

---

## Ejemplo 7: Reporte para Board/Investors

```markdown
Genera reporte ejecutivo para C-Suite

Audiencia:
- CEO/CFO
- Board of Directors
- Investors

Contenido:
1. Executive Summary (1 página)
   - Risk assessment overall
   - Bottom line recommendation
   - Financial impact estimate

2. Key Findings (1 página)
   - Top 3 hallazgos críticos
   - Business impact de cada uno
   - Timeline de remediación

3. Remediation Plan (1 página)
   - Investment required
   - Timeline
   - Team size
   - Expected outcome

4. Compliance Status (1 página)
   - PCI/GDPR/NIST gaps
   - Remediation roadmap
   - Timeline to compliance

Total: 4 páginas profesionales

Tono: Ejecutivo, no técnico
Incluir: Impacto en negocio, riesgo financiero, timeline
```

**Tiempo**: 2-4 horas  
**Audiencia**: C-Suite

---

## Ejemplo 8: Reporte Anual de Seguridad

```markdown
Genera reporte anual consolidado

Período: Enero 2025 - Enero 2026

Contenido:
1. Overview de Evaluaciones
   - Total de apps evaluadas
   - Línea de tiempo de testing
   - Recursos utilizados

2. Hallazgos por Vector OWASP
   - Distribución de vulnerabilidades
   - Trends (mejoría/empeoramiento)
   - Comparación año anterior

3. Remediación Progress
   - Hallazgos resueltos: 85%
   - Tiempo promedio de remediación
   - Hallazgos aún open por edad

4. Compliance Status
   - PCI-DSS: 92% compliant
   - GDPR: 87% compliant
   - NIST: 78% compliant
   - ISO 27001: 89% compliant

5. Insights & Recommendations
   - Patrones de vulnerabilidades
   - Mejoras para siguiente año
   - Inversiones de seguridad recomendadas

6. Appendix
   - Detalles técnicos
   - Metodología
   - Herramientas utilizadas
```

**Tiempo**: 1 semana de compilación  
**Audiencia**: Board, Management, Security Team

---

**Nota**: Todos estos prompts son templates. Ajústalos según tu contexto específico.

