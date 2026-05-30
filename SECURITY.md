# Security Policy — COALA SwarmOps

## Supported Versions

| Version | Tier Coverage | Security Updates |
|---------|--------------|------------------|
| **v6.7** | T0-T3 · 21 agents · SDD pipeline | ✅ Active |
| **v6.5** | T0-T3 · 18 agents | ✅ Active |
| **v6.2** | Operational stable swarm | ⚠️ Critical fixes only |
| **< v6.2** | Experimental | ❌ Unsupported |

## Reporting a Vulnerability

**Do NOT open a public GitHub Issue for security vulnerabilities.**

Instead, report them privately:

- **Email:** [security contact — add your email here]
- **Expected response:** Within 48 hours
- **Disclosure policy:** We follow coordinated disclosure. Fix is released before the vulnerability is publicly disclosed. You will be credited in the release notes (unless you prefer anonymity).

### What to Include

1. Description of the vulnerability
2. Steps to reproduce
3. Affected versions
4. Potential impact
5. Suggested fix (if any)

## Security Architecture

COALA SwarmOps follows security-by-design principles:

| Layer | Protection |
|-------|-----------|
| **T0 (Local)** | Ollama models run locally. No data leaves the machine. |
| **T1-T3 (Cloud)** | API keys never stored in repo. Providers isolated per tier. |
| **SDD Pipeline** | 5 gates + Security Auditor (T2) validates every PR before merge. |
| **OWASP Top 10** | Baseline security checks on all generated code. |
| **PCI-DSS** | Compliance checks for payment-related features (tancerca). |
| **Dependency Scanning** | Planned for v7.0 — automated `npm audit` / `pip-audit` in CI. |

## Security Best Practices for Users

1. **Never commit `apikey` files** — they are in `.gitignore`
2. **Use environment variables** for all API keys
3. **Rotate keys** every 90 days
4. **Review generated code** — the Security Auditor validates, but human review adds defense-in-depth
5. **Keep Ollama updated** — local models receive security patches

## Vulnerability Disclosure History

| Date | Severity | Description | Fix Version |
|------|----------|-------------|-------------|
| — | — | No vulnerabilities disclosed yet | — |

---

*We take the security of our swarm ecosystem seriously. Thank you for helping keep COALA SwarmOps safe.*
