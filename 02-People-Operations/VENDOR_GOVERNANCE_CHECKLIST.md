# 🤝 Vendor & Offshore Governance Checklist
> **Purpose:** To ensure that external partners (SIs/Managed Services) maintain technical parity with internal engineering standards and deliver measurable ROI.

---

## 🏗️ 1. Technical Integration & Standards
*Before a single script is written, the vendor must demonstrate compliance with the [Automation Standards](../03-Operational-Delivery/AUTOMATION_STANDARDS_GOVERNANCE.md).*

- [ ] **Environment Parity:** Does the vendor have access to the exact same CI/CD pipelines and Dockerized environments as internal teams?
- [ ] **Code Quality Gates:** Are vendor PRs subject to the same [Automation Review Checklist](../03-Operational-Delivery/AUTOMATION_STANDARDS_GOVERNANCE.md)?
- [ ] **Technical Debt Cap:** Is the vendor responsible for refactoring their own code? (Target: < 10% of sprint capacity).
- [ ] **Tooling Alignment:** Is the vendor using the approved stack (e.g., Playwright/Rest-Assured) vs. proprietary "black-box" tools?

---

## 📈 2. Delivery & Metric Accountability
*Vendors are measured against the [People Metrics](./PEOPLE_METRICS.md) and [QA Metrics](../04-Business-Value-ROI/QA_METRICS_DASHBOARD.md).*

- [ ] **Defect Rejection Rate:** Are < 5% of vendor-logged bugs being rejected as "Not a Bug"?
- [ ] **Automation Velocity:** Is the vendor automating > 80% of the features they are assigned to test?
- [ ] **SLA Compliance:** Are P0/P1 bugs triaged within the agreed 4-hour window?
- [ ] **Outcome-Based Billing:** Are payments tied to deliverables (e.g., "Feature Automation Complete") rather than just "Hours Logged"?

---

## 🧠 3. Knowledge Retention & Security
*Ensuring the "Bus Factor" remains low and company IP is protected.*

- [ ] **Bi-Weekly Demos:** Does the vendor walk internal leads through their framework contributions?
- [ ] **Living Documentation:** Are the repository READMEs and Confluence pages updated in real-time?
- [ ] **Security Compliance:** Have all offshore testers completed PII/GDPR training for the specific domain?
- [ ] **Offboarding Protocol:** Is there a "Knowledge Transfer (KT) Pack" ready for every contractor roll-off?

---

## 🏆 4. The "One Team" Culture
- [ ] **Ceremony Participation:** Does the vendor attend Sprint Planning and Retrospectives as peers, not "order takers"?
- [ ] **Recognition:** Are high-performing offshore SDETs recognized in the same "Team Shout-outs" as internal staff?