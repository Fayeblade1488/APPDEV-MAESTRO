# Automated Compliance, Reporting, & How‑to Guide

## 1. Automated Compliance & Reporting

> **Note:** `appdev-maestro-verification.yml` is a **machine‑executable** test plan, not just documentation.

### 1.1 Test Harness

Your automated test runner should be configured to parse `appdev-maestro-verification.yml` and discover each test case.

### 1.2 Execution

Honor the following attributes on each test case:

* `timeout`: maximum duration to wait for a response (e.g., `10s`, `60s`).
* `retries`: number of automatic re‑runs on failure.

### 1.3 Reporting

1. Emit a **JUnit‑style XML report** on any test failures.
2. Automatically send the report (and any logs) to **internal‑sys‑arch\@acme‑corp.com**.

### 1.4 Governance & Contact

* **License:** Proprietary (as defined in the manifest).
* **Failure Contact:** `internal‑sys‑arch@acme‑corp.com`.

---

## 2. Overview

AppDev‑Maestro is your turnkey, YAML-driven AI persona for macOS & Google Gemini application development. Think of it as a 24/7 consultant—no billing cycle required. This guide covers quickstart, do’s & don’ts, best practices, and troubleshooting to keep your CI/CD pipeline humming.

---

## 3. Quickstart

1. **Clone the repo**

   ```bash
   git clone git@repo.acme-corp.com:maestro/appdev-maestro.git
   cd appdev-maestro
   ```
2. **Validate the manifest** (blocking CI step)

   ```bash
   yamllint .
   ```
3. **Wire up the test harness**

   * Point your runner at `appdev-maestro-verification.yml`.
   * Honor each test case's `timeout` and `retries`.
4. **Deploy & Monitor**

   * Bundle `*.yml`, `README.md`, and this guide into a versioned release.
   * Hook automated failure alerts to `internal-sys-arch@acme-corp.com`.

---

## 4. Do’s & Don’ts

### Do’s

* Treat YAML modules as **source‑of‑truth**—never hand‑edit generated files.
* Document every change in the `CHANGELOG` section of the framework file—auditors love a clear trail.
* Enforce `yamllint` in pre‑commit hooks or CI pipelines for zero‑drift.
* Respect the `SAFEGUARDS` section for security‑testing scenarios.

### Don’ts

* Don’t hard‑code API keys or secrets in client‑side code—use env vars or serverless proxies.
* Don’t ignore test failures; treat any `FAIL` criteria as a red flag requiring immediate remediation.
* Don’t deviate from ISO‑8601 timestamps in the `METADATA` section (e.g., `2025-07-08T14:30:00Z`).

---

## 5. Best Practices

| Area              | Recommendation                                                                                    |
| ----------------- | ------------------------------------------------------------------------------------------------- |
| **Versioning**    | Follow [Semantic Versioning](https://semver.org): `MAJOR.MINOR.PATCH`.                            |
| **Modularity**    | Keep persona, manifest, and verification in separate modules. |
| **CI/CD**         | Automate linting (`yamllint`), test harness execution, and packaging in your pipeline.             |
| **Docs**          | Maintain a live `CHANGELOG` and this guide alongside your YAML artifacts.                    |
| **Security**      | Proxy all API calls through serverless functions—never expose keys to the front end.              |
| **Monitoring**    | Integrate test harness results into dashboards (GitHub Actions, Jenkins, GitLab CI).              |
| **Collaboration** | Use branch‑based workflows. Require PRs and linter validation before merging.                     |

---

## 6. Troubleshooting

* **YAML validation fails?**

  1. Check for indentation errors or incorrect syntax.
  2. Run `yamllint .` to get a detailed error report.
* **Test harness hangs or time‑outs?**

  * Verify the `timeout` / `retries` attributes in the failing test case. Adjust if legitimately long.
* **Missing module errors?**

  * Ensure your CI artifact bundle contains ***all*** YAML files.

---

## 7. Contact & Support

* **License & Governance Questions:** Refer to the `LICENSE` section in the manifest.
* **General Help:** Standard Github practices.
