# 🏛️ Master Test Strategy (MTS)
> **Standard:** TMMi Level 2 (Managed) & ISO 29119 Compliant  
> **Scope:** Enterprise-wide testing standards for all squads.

---

## 1. 🎯 Objectives & Scope
This document defines the mandatory testing standards to ensure every release meets the business's quality requirements.
* **Goal:** 100% visibility on product risk prior to deployment.
* **In-Scope:** All Web, Mobile, and API services within the domain.
* **Out-of-Scope:** Third-party vendor internal code (Black-box only).

---

## 2. ⚖️ Risk-Based Testing (RBT) Approach
We do not test everything equally. We use the **Analytical Strategy** (Risk-Based):
1. **Risk Identification:** Performed during the [Three Amigos](../02-People-Operations/TEAM_WORKING_AGREEMENT.md).
2. **Prioritization:** Using the [RBT Priority Matrix](./RBT_PRIORITY_MATRIX.md).
3. **Execution Depth:** - **Critical Risk:** Automated Regression + Manual Exploratory + Full API Contract Test.
   - **Low Risk:** Developer Self-QA + Automated Smoke Test only.

---

## 🏗️ 3. Test Levels & Types
To achieve "Shift-Left," testing is distributed across these standard levels:

| Level | Responsibility | Type | Focus |
| :--- | :--- | :--- | :--- |
| **L1: Unit** | Developer | Automated | Logic, boundary values, methods. |
| **L2: Integration** | Dev/QA | Automated | API Contracts, internal dependencies. |
| **L3: System** | QA | Hybrid | End-to-End User Journeys (UI). |
| **L4: Acceptance**| PO/UAT | Manual | Business value, usability, legal compliance. |

---

## 🚦 4. Entry & Exit Criteria (The Gates)
No feature moves forward unless it passes these "Managed" criteria.

### Entry Criteria (Ready to Test)
* Requirements signed off in Gherkin format.
* Test Data is available and sanitized.
* Code has passed L1 Unit Tests with >80% coverage.

### Exit Criteria (Ready to Ship)
* 100% of "High Risk" test cases executed and passed.
* Zero "Blocker" or "Critical" defects open.
* [Blameless RCA](../03-Operational-Delivery/BLAMELESS_RCA.md) conducted for any found production-like defects in Staging.

---

## 🛠️ 5. Test Environment & Data
* **Environments:** Development (Isolated), Staging (Production-like), Production.
* **Data Strategy:** Synthetic data generation using Gen AI for PII-sensitive flows. No live customer data in non-prod environments.

---

## 📊 6. Defect Management
* **Tool:** Jira
* **Severity Levels:** - **S1 (Blocker):** Immediate fix required; stops the release.
  - **S2 (Critical):** Core functionality broken; no workaround.
  - **S3 (Major):** Functionality broken; workaround exists.
  - **S4 (Minor):** UI/UX polish issues.

---

## 🔄 7. Regression Strategy
* **Automated Smoke:** Runs on every PR (Gate 1).
* **Automated Regression:** Runs nightly (Gate 3).
* **Manual Regression:** Only performed if AI-driven risk analysis suggests an "Impact Gap."

---

## 🎓 8. Governance & Maintenance
* This MTS is reviewed annually or after any [Major Post-Mortem](./BLAMELESS_RCA.md).
* All squads must align their local "Sprint Test Plans" to this Master Strategy.
