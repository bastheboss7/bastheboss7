# ⚖️ Risk-Based Testing (RBT) Matrix
> **Philosophy:** "Test what matters." Allocate manual testers where critical thinking wins, and automation where repeatability scales.

This matrix is the bridge between **business priorities** and **testing resources**. It answers: *What should we test manually vs. automate?*

## The Decision Framework

| Feature Area | Business Impact | Failure Risk | Risk Score | Testing Strategy |
| :--- | :---: | :---: | :---: | :--- |
| **Primary Login (Happy Path)** | 5 | 1 | 5 | **Automated (Sanity)** - Regression baseline |
| **MFA / 2FA Verification Flow** | 5 | 3 | 15 | **Manual + Automated** - Expert judgment + coverage |
| **Account Recovery (Lost Password)** | 4 | 4 | 16 | **Primary: Manual** - User empathy & edge cases first |
| **UI Localization (Labels/Links)** | 1 | 1 | 1 | **Manual Spot-Check** - Occasional human eye |
| **OAuth 3rd Party Integration** | 4 | 3 | 12 | **API Automation** - Contract validation + integration |

## Risk Score Strategy

- **Risk 15-25 (Critical):** Stop-ship issues. Pair manual exploratory testing with automated regression checks. Manual testers first.
- **Risk 8-14 (Medium):** Mix manual for new features + automation for regression. Balance required.
- **Risk 1-7 (Low):** Lighter touch. Automation-first, occasional manual verification.

---
This matrix is to translate Risk Scores into specific Manual vs. Automation effort allocations.

## 🧮 The Scoring Formula
**Risk Score = Impact (1-5) × Probability (1-5)**

| Score | Category | Strategy |
| :--- | :--- | :--- |
| **15-25** | 🔴 **Critical** | **Exhaustive:** 100% Automation + Senior Manual Exploratory. |
| **8-14** | 🟡 **Medium** | **Hybrid:** Manual for new logic; Automation for regression. |
| **1-7** | 🟢 **Low** | **Minimal:** Automated Smoke Test only; Manual on-demand. |

---

## 🛠️ Execution Worksheet (Sprint Template)

Use this table during the **Three Amigos** or **Sprint Planning** to define the "Definition of Done."

| Feature Name | Risk Score | Logic Type | Manual Requirement | Automation Requirement |
| :--- | :---: | :--- | :--- | :--- |
| **Example: Apple Pay Integration** | **25** | New | 3 days Exploratory (Edge cases, network drops). | 100% Path Coverage (API + UI). |
| **Example: Update Footer Links** | **2** | Existing | None (Spot check only). | None (Handled by Global Smoke). |
| **Example: Search Filter v2** | **12** | New | 1 day Functional UI testing. | Automate "Happy Path" only. |

---

## 🔍 Deep Dive: Critical Logic Strategy (Score 15-25)

### 1. New Critical Logic (Discovery Focus)
* **Mandatory:** 1x Senior Peer Review of the Test Plan.
* **Technique:** **Negative Testing** (Invalid inputs, SQL injection attempts, concurrency checks).
* **Exit Criteria:** 0 Open Defects of any severity.

### 2. Existing Critical Logic (Protection Focus)
* **Mandatory:** **Impact Analysis** document showing which modules are touched.
* **Technique:** **Regression Suite** (Must pass 100% in Gate 3).
* **Exit Criteria:** No regression found in core "Golden Flows."
