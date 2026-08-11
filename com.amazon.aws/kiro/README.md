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
