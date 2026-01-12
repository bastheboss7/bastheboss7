# 🔍 Blameless Root Cause Analysis (RCA)

> **Our Core Principle:** Incidents are opportunities to improve our systems, not to blame individuals. We believe every incident has multiple contributing factors, and our goal is to fix the system, not the person.

This document outlines a structured, blameless process for analyzing incidents to drive continuous improvement.

---

## 🎯 When to Conduct an RCA

An RCA should be triggered for any of the following events:
-   **Production Incidents:** Any issue that has a direct impact on customers.
-   **Escaped Defects:** Critical bugs that were missed in testing and discovered in production.
-   **Process Breakdowns:** Failures caused by not following established processes, such as skipping the [Three Amigos](./THREE_AMIGOS_CHECKLIST.md) or not applying the [RBT Priority Matrix](./../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md).
-   **Near-Misses:** Critical issues that were caught just before a release, indicating a gap in the process.

---

## ⚙️ The RCA Process: A 5-Whys, Systems-Focused Approach

We use the "5 Whys" technique to systematically drill down to the root cause of an issue, focusing on system and process failures rather than individual errors.

### Example: Login Failure in Dark Mode

-   **What Happened?** The login feature failed for users on Safari with Dark Mode enabled, blocking a critical user path.
-   **Impact:** A 45-minute outage for 2% of users, leading to customer frustration and potential brand damage.

| Question | Answer | Root Cause Category |
|----------|--------|---------------------|
| **Why did login fail?** | A CSS layer overlapped the "Sign In" button, making it unclickable. | Technical Defect |
| **Why wasn't this caught in testing?** | The automated test suite only ran in Light Mode. | Automation Strategy Gap |
| **Why wasn't Dark Mode tested?** | The risk assessment did not include UI theming as a factor. | Exploratory Testing Gap |
| **Why wasn't Dark Mode considered high-risk?** | It was labeled a "UI enhancement," not a critical path feature. | Risk Classification Error |
| **Why did we misclassify the risk?** | Our [RBT Priority Matrix](./../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md) did not account for theme variations. | Process Gap |

---

## 🤖 Gen AI-Assisted RCA (Accelerator)

We leverage Gen AI to accelerate the RCA process, but human judgment remains central.

-   **Automated Analysis:** An AI can ingest logs and test results to identify patterns and suggest potential root causes.
-   **Intelligent Triage:** An LLM can help classify the incident (e.g., automation gap vs. process gap).
-   **Drafting the RCA:** Gen AI can draft the initial RCA document, which humans then validate and refine.

*Note: Gen AI is a tool to augment our analysis; it does not replace our commitment to a blameless, learning-focused culture.*

---

## 💡 Key Insights (Not Blame)

From the example above, the key takeaways are system-level improvements, not individual faults:
-   **Automation Gap:** Our test suite lacked coverage for different UI themes.
-   **Manual Gap:** Our exploratory testing charters did not include guidance on theme-related risks.
-   **Process Gap:** Our risk assessment framework needed to be updated to include visual and theme variations.

---

## 🛠️ Corrective Actions (Process-Oriented)

### Immediate (Within 24 hours)
-   [ ] **Automation:** Add Dark Mode to the Playwright test configuration.
-   [ ] **Manual:** Brief the team on visual regression scenarios to test.

### Structural (Next Sprint)
-   [ ] **RBT Update:** Add "Visual & Theme Combinations" to the critical path assessment in the [RBT Priority Matrix](./../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md).
-   [ ] **Three Amigos Update:** Add a "Theme & Accessibility Verification" item to the [Three Amigos Checklist](./THREE_AMIGOS_CHECKLIST.md).

### Long-Term (1-3 Months)
-   [ ] **Tooling:** Implement an automated visual regression tool (e.g., Playwright with Percy).
-   [ ] **Training:** Conduct a workshop on accessibility-first testing, including Dark Mode and WCAG compliance.

---

## 💬 The Blameless RCA Meeting

-   **Attendees:** Dev Lead, QA Lead, Product Manager, and the engineers involved.
-   **Tone:** The conversation is driven by curiosity, not judgment. We ask, "How did we miss this?" not "Who made a mistake?"
-   **Focus:** The discussion centers on improving the system to prevent the issue from recurring.

## Why This Matters

💡 **Blameless RCA = Better Systems**  
- Teams speak up about issues (no fear of punishment)
- Root causes get addressed (not superficial blame)
- Learning spreads across team (everyone benefits)
- Automation + manual testing both improve together

💡 **Blame-Based RCA = Worse Outcomes**  
- Teams hide near-misses (to avoid blame)
- Same mistakes repeat (root causes ignored)
- Culture of fear (people protect themselves)
- Automation and manual testers blame each other

---
## 📈 RCA Action Tracker (Sprint Governance)
*This table tracks the permanent process improvements derived from RCAs.*

| Incident ID | Root Cause | Permanent Action Taken | Status |
| :--- | :--- | :--- | :--- |
| RCA-001 | Missing Unit Test for Auth Edge Case | Updated **Gate 1** to include 95% coverage for Auth module. | ✅ Done |
| RCA-002 | Staging DB out of sync with Prod | Integrated **Automated Schema Validation** into Gate 2. | 🛠️ In Progress |
