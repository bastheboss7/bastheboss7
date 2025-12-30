# 🛡️ Quality Gates & Production Readiness Criteria
> **Standard:** TMMi Level 5 (Optimized) | **Strategic Focus:** Scalable Quality for 5:1 Dev-to-QA Ratios

Quality Gates are the non-negotiable checkpoints in our CI/CD pipeline. These gates ensure that even with a lean test team, no feature reaches production without meeting our high-trust stability standards.



---

### 🚪 Gate 1: Code Commit (Developer Level)
*Owner: Engineering Team | Tooling: Pre-commit hooks / Husky*

- [ ] **Linting:** 0 Errors in TypeScript/Java (ESLint/Checkstyle).
- [ ] **Unit Test Coverage:** Minimum **80% line coverage** for new logic.
- [ ] **Shift-Left A11y:** Local 'Axe-core' pass on all modified UI components.

### 🚪 Gate 2: Pull Request (Peer & CI Level)
*Owner: GitHub Actions & Senior Engineers*

- [ ] **Peer Review:** Minimum of one "Approve" from a Senior Developer.
- [ ] **Smoke Suite:** Playwright/Appium 'Smoke' tag must pass 100% on **Web & Mobile (BrowserStack)**.
- [ ] **Static Analysis:** No high-severity vulnerabilities detected in security scans (Snyk/SonarQube).

### 🚪 Gate 3: Integration (The RBT Gate)
*Owner: 1 Automation Tester & 1 Manual Tester*

- [ ] **RBT Validation:** All **High-Risk (Score 15-25)** features must have 100% manual exploratory sign-off.
- [ ] **Automation (AT):** All "In-Sprint" automated scripts for **High/Medium Risk** features must be merged and passing.
- [ ] **Observability:** Error logs must be validated as "Clear and Concise" (No vague 'Error' strings).

### 🚪 Gate 4: Release Readiness (Leadership Level)
*Owner: Lead QA Consultant*

- [ ] **Defect Density:** Zero open 'Critical' or 'Major' defects.
- [ ] **The 10-Minute Rule:** Pipeline suites must complete in <10 mins to maintain release velocity.
- [ ] **RCA Closure:** Any blockers from the previous sprint must have a completed **Blameless RCA**.

---

> [!IMPORTANT]
> **The Hard Stop Rule:** Any failure in Gate 1 or 2 automatically blocks the merge. Failures in Gate 3 or 4 require a formal "Risk Waiver" signed by the Lead QA Consultant and the Product Owner.

---

### ⚖️ Emergency Override Protocol
In the event of a critical production hotfix where speed is the priority:
1. **Risk Evaluation:** Re-calculate the [RBT Score](./RBT_PRIORITY_MATRIX.md).
2. **Post-Release Debt:** A "Regression Catch-up" must be scheduled within 24 hours of the hotfix.
3. **Audit Trail:** Document the reason for the bypass in the next Sprint Retrospective.

---

### 🧠 Leadership Philosophy
By implementing these gates, we move away from "Rude" or "Policing" management. The **system** enforces the quality, allowing the Lead to act as a **Mentor** rather than a "Gatekeeper."
