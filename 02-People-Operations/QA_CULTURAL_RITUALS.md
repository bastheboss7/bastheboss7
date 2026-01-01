# 🎭 QA Cultural Rituals & Best Practices
> **Philosophy:** A framework is only as good as the culture that supports it. We use these "rituals" to ensure our engineering standards remain living, breathing assets.

---

## 🐣 1. The "Pay It Forward" Onboarding (Self-Healing Docs)
**Practice:** Every new starter is the "Owner" of the Onboarding Documentation for their first 30 days.
* **The Task:** They must identify one gap, one outdated step, or one missing link in the [Onboarding Starter Kit](./RESOURCING_STRATEGY.md).
* **The Goal:** Before they finish their first month, they must submit a PR to improve the onboarding flow for the *next* person.
* **Result:** Documentation that never rots and a new hire who feels immediate "Code Ownership."

---

## 🛡️ 2. The "Bug Bounty" for Technical Debt
**Practice:** One day per month (or a percentage of every sprint) is dedicated to "Refactor Friday."
* **The Focus:** No new features. The team focuses on:
    * Reducing [The Toil Ratio](./PEOPLE_METRICS.md).
    * Updating fragile selectors in [Playwright/Selenium](../03-Operational-Delivery/AUTOMATION_STANDARDS_GOVERNANCE.md).
    * Optimizing API mocks.
* **Result:** Prevents the "Automation Debt Trap" and keeps the [ROI Model](../04-Business-Value-ROI/AUTOMATION_ROI_MODEL.md) positive.

---

## 🧪 3. "Shadow-the-Dev" Days
**Practice:** SDETs spend one day per quarter sitting with a Developer to watch them code and run local builds.
* **The Goal:** To understand the "Developer Experience" (DX). 
* **Insight:** If the automation is too slow for the dev to run locally, the SDET must find ways to [Shard or Optimize](../01-Strategic-Governance/TECHNOLOGY_STACK.md) the suite.

---

## 📣 4. The "Three Amigos" is Non-Negotiable
**Practice:** No ticket moves from "To Do" to "In Progress" without a 10-minute sync between Dev, QA, and PO.
* **The Output:** Agreement on the **Definition of Done (DoD)** and the core [RBT Priority](../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md).
* **Result:** Zero ambiguity and massive reduction in "Requirement Bugs."

---

## 🧹 5. The "Clean-As-You-Go" Data Policy
**Practice:** No test should rely on existing state. Every test is responsible for its own "Birth" and "Death."
* **The Standard:** If a test creates a User via API, it must delete/archive that User in the `afterAll` hook or fixture. 
* **Result:** Flawless parallel execution and stable environments.