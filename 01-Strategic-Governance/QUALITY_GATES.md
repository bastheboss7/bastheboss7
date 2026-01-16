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

### 🤖 Automation Enforcement (Gate 3)
To ensure Gate 3 is both thorough and performant, we utilize a **Tiered Automation Execution** model. Execution is governed by metadata tags assigned during development based on the [RBT Score](./RBT_PRIORITY_MATRIX.md).

* **Mandatory Pass:** All tests tagged `@smoke` (Critical Path) must pass 100%.
* **Regression Requirement:** Tests tagged `@regression` (High/Medium Risk) must pass >98%.

### 🚪 Gate 4: Release Readiness (Leadership Level)
*Owner: Lead QA Consultant*

- [ ] **Defect Density:** Zero open 'Critical' or 'Major' defects.
- [ ] **The 10-Minute Rule:** Pipeline suites must complete in <10 mins to maintain release velocity.
- [ ] **RCA Closure:** Any blockers from the previous sprint must have a completed **Blameless RCA**.

### 🚪 Gate 5: Post-Deployment Monitoring (Live)
*Owner: QA Unit | Tooling: Playwright, New Relic/Sentry*

- [ ] **Synthetic Production Smoke:** Playwright scripts running every 15 mins in Prod for core flows (MFA/Login).
- [ ] **Real-User Monitoring (RUM):** Integrating with tools like New Relic/Sentry to monitor JS errors in the wild.
- [ ] **Alerting:** Automated Slack triggers for any failure in the Production Smoke suite.

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

## 📱 App Store Intelligence & Device Strategy
We treat the **Google Play** and **Apple App Store** as our most honest "QA environment."

* **Sentiment Analysis:** Weekly audit of ratings < 3 stars.
* **Evidence-Based Reproduction:** When a user reports a crash, we use the specific device/OS combination (e.g., Samsung S22/Android 14) from our **Cloud Grid (BrowserStack)** to reproduce.
* **Closing the Loop:** Every "1-star" bug reproduction is tagged as a High-Priority RCA to prevent recurrence.

---

## 📈 Strategic Resource Reinvestment
In a balanced team, we do not waste surplus time on low-value testing. Instead, we convert "Surplus Capacity" into **Technical Equity**.

### When the [RBT Matrix](./RBT_PRIORITY_MATRIX.md) shows Low Risk:
| Reinvestment Area | Activity |
| :--- | :--- |
| **Innovation Backlog** | Building AI-driven test data generators for Developers. |
| **Chaos Engineering** | Injecting failures into API mocks to test system resilience. |
| **Performance Budgets**| Baselining API response times to prevent "Speed Creep." |
| **Framework Pruning** | Reducing CI/CD execution time to meet the **10-Minute Rule**. |

---

### 🧠 Leadership Philosophy
By implementing these gates, we move away from "Rude" or "Policing" management. The **system** enforces the quality, allowing the Lead to act as a **Mentor** rather than a "Gatekeeper."

> "We don't just wait for the next sprint. By monitoring the App Store and running Production Smoke tests, we act as the **Voice of the Customer**. When the workload is light, we don't idle; we engineer the tools that will make the *next* high-risk sprint move faster."
