# Security Policy

## Supported Versions

| Version    | Supported          | Notes                                    |
| ---------- | ------------------ | ---------------------------------------- |
| `v1.4.x`   | ✔️ Active support  | Latest production release.               |
| `v1.3.x`   | ❌ End of Life     | No longer receiving security updates.    |
| `< v1.3`   | ❌ End of Life     | Please upgrade to `v1.4.x`.              |

## Reporting a Vulnerability

If you discover a security vulnerability in AppDev-Maestro, please report it **privately**:

1. **Email**: `annabear2213@gmail.com`   
2. **Subject**: `[SECURITY] <short vulnerability title>`  

Please include:
- A clear description of the issue and its potential impact.
- Steps to reproduce (proof-of-concept code, input data, screenshots).
- Affected version(s).
- Your contact info (email, Twitter, etc.) for follow-up questions.

We will acknowledge receipt within **48 hours** and aim to provide a remediation plan within **7 days**.  

## Security Response Process

| Phase                   | SLA       |
| ----------------------- | --------- |
| Acknowledgment          | 48 hours  |
| Initial Triage & Scope  | 72 hours  |
| Patch & Validation      | 7 days    |
| Public Disclosure       | ASAP after patch release (coordinated) |

1. **Triage** — We confirm the issue, assess severity, and assign a CVSS score.  
2. **Fix** — We develop, test, and QA a fix.  
3. **Release** — We publish a patch (or point release) and update `CHANGELOG.md`.  
4. **Disclosure** — We coordinate a public advisory (GitHub Security Advisory + release notes).

## Security Best Practices

- **Keep Dependencies Up-to-Date**  
  Run `npm audit` or your language’s vulnerability scanner regularly.
- **Use Strict Permissions**  
  Limit service accounts, database creds, and API tokens to the minimum scope.
- **Rotate Secrets**  
  Store secrets in a vault (e.g., AWS Secrets Manager, Vault) and rotate every 90 days.
- **Enable Monitoring & Alerts**  
  Log all failed auth attempts, unexpected exceptions, and high-rate API calls.

## Reporting Disclosures

Once a fix is available, we will:
- Publish a **GitHub Security Advisory**.
- Tag the patched release (e.g. `v1.4.1`).
- Merge a short **ADVISORY.md** into the repo describing CVE details.

## Acknowledgments

Thank you to the security researchers and community members who help keep AppDev-Maestro safe and secure. All reporters will be credited in the next minor release’s **CHANGELOG.md** (unless you request anonymity).

---

*This policy was last updated on `2025-07-08`.*
