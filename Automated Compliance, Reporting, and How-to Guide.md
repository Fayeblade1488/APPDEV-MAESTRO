# Automated Compliance, Reporting, & How‑to Guide

## 1. Automated Compliance & Reporting

> **Note:** `appdev-maestro-verification.xml` is a **machine‑executable** test plan, not just documentation.

### 1.1 Test Harness

Your automated test runner should be configured to parse `appdev-maestro-verification.xml` and discover each `<adm:TEST_CASE>`.

### 1.2 Execution

Honor the following attributes on each test case:

* `timeout`: maximum duration to wait for a response (e.g., `10s`, `60s`).
* `retries`: number of automatic re‑runs on failure.

### 1.3 Reporting

1. Emit a **JUnit‑style XML report** on any test failures.
2. Automatically send the report (and any logs) to **internal‑sys‑arch\@acme‑corp.com**.

### 1.4 Governance & Contact

* **License:** Proprietary (as defined in `<adm:LICENSE>` of the manifest).
* **Failure Contact:** `internal‑sys‑arch@acme‑corp.com`.

---

## 2. Overview

AppDev‑Maestro is your turnkey, schema‑driven AI persona for macOS & Google Gemini application development. Think of it as a 24/7 consultant—no billing cycle required. This guide covers quickstart, do’s & don’ts, best practices, and troubleshooting to keep your CI/CD pipeline humming.

---

## 3. Quickstart

1. **Clone the repo**

   ```bash
   git clone git@repo.acme-corp.com:maestro/appdev-maestro.git
   cd appdev-maestro
   ```
2. **Validate the manifest** (blocking CI step)

   ```bash
   xmllint --noout \
     --schema appdev-maestro.xsd \
     appdev-maestro-framework.xml
   ```
3. **Wire up the test harness**

   * Point your runner at `appdev-maestro-verification.xml`.
   * Honor each `<adm:TEST_CASE>`’s `timeout` and `retries`.
4. **Deploy & Monitor**

   * Bundle `*.xml`, `appdev-maestro.xsd`, `README.md`, and this guide into a versioned release.
   * Hook automated failure alerts to `internal-sys-arch@acme-corp.com`.

---

## 4. Do’s & Don’ts

### Do’s

* Treat XML modules as **source‑of‑truth**—never hand‑edit generated files.
* Bump the `version` attribute **and** update `xsi:schemaLocation` in lock‑step.
* Document every change in `<adm:CHANGELOG>`—auditors love a clear trail.
* Enforce `xmllint` in pre‑commit hooks or CI pipelines for zero‑drift.
* Respect `<adm:SAFEGUARDS action="BLOCK_NONE">` for security‑testing scenarios.

### Don’ts

* Don’t rename or remove the `adm:` namespace prefix—schema validation will fail.
* Don’t omit `<xi:fallback>` blocks on any new `<xi:include>` entries.
* Don’t hard‑code API keys or secrets in client‑side code—use env vars or serverless proxies.
* Don’t ignore test failures; treat any `<adm:FAIL>` as a red flag requiring immediate remediation.
* Don’t deviate from ISO‑8601 timestamps in `<adm:METADATA>` (e.g., `2025-07-08T14:30:00Z`).

---

## 5. Best Practices

| Area              | Recommendation                                                                                    |
| ----------------- | ------------------------------------------------------------------------------------------------- |
| **Versioning**    | Follow [Semantic Versioning](https://semver.org): `MAJOR.MINOR.PATCH`.                            |
| **Modularity**    | Keep persona, manifest, and verification in separate modules; use `<xi:include>` for composition. |
| **CI/CD**         | Automate linting (`xmllint`), test harness execution, and packaging in your pipeline.             |
| **Docs**          | Maintain a live `<adm:CHANGELOG>` and this guide alongside your XML artifacts.                    |
| **Security**      | Proxy all API calls through serverless functions—never expose keys to the front end.              |
| **Monitoring**    | Integrate test harness results into dashboards (GitHub Actions, Jenkins, GitLab CI).              |
| **Collaboration** | Use branch‑based workflows. Require PRs and schema validation before merging.                     |

---

## 6. Troubleshooting

* **Schema validation fails?**

  1. Check for stray or mismatched tags.
  2. Ensure your `appdev-maestro.xsd` matches the version in `xsi:schemaLocation`.
* **Test harness hangs or time‑outs?**

  * Verify the `timeout` / `retries` attributes in the failing `<adm:TEST_CASE>`. Adjust if legitimately long.
* **Missing module errors on include?**

  * Confirm `xml:base` is correct for your deployment.
  * Ensure your CI artifact bundle contains ***all*** XML files.

---

## 7. Contact & Support

* **License & Governance Questions:** Refer to `<adm:LICENSE>` in the manifest.
* **General Help:** Standard Github practices.
