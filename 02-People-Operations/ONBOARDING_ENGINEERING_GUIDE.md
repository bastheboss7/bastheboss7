# 🤝 Team Onboarding: The High-Trust QA Way
> **Welcome to the Team!** This guide will help you navigate our Level 5 TMMi environment and our 5:1 Dev-to-QA ratio.

As a Lead Consultant, I value **Autonomy over Micro-management**. This document explains the standards you need to follow so we can ship high-quality code at Sky-speed.

---

### 1. 🎯 Your First 48 Hours
Your goal is to understand our **[Quality Gates](../01-Strategic-Governance/QUALITY_GATES.md)**.
- **Day 1:** Set up your local environment (Playwright, Node.js, Docker).
- **Day 1:** Review the **[Team Working Agreement](./TEAM_WORKING_AGREEMENT.md)**—this is how we treat each other.
- **Day 2:** Shadow a **Three Amigos** session to see how we "Shift-Left."

---

### 2. ⚖️ Decision Making: The RBT Rule
We do not test everything. Before you start a ticket:
1. Open the **[RBT Priority Matrix](../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md)**.
2. If a ticket is **High Risk**, you own the "In-Sprint Automation" AND the "Manual Exploratory" charter.
3. If a ticket is **Low Risk**, you are authorized to delegate the testing to the Developer using the **[Self-QA Checklist](../03-Operational-Delivery/DEV_SELF_QA_CHECKLIST.md)**.

---

### 🔄 3. The Sprint Workflow (10-Day Cycle)



| Days | Phase | Your Responsibility |
| :--- | :--- | :--- |
| **1-2** | Refinement | Challenge requirements. Define "Success Criteria" in Gherkin. |
| **3-5** | Skeleton Phase | **Automation:** Write Page Objects. **Manual:** Create Exploratory Charters. |
| **6-8** | Execution | Execute tests. If it's High Risk, it needs a 100% pass on both UI and API. |
| **9-10** | Hardening | Prune old tests. Perform a **[Blameless RCA](../03-Operational-Delivery/BLAMELESS_RCA.md)** for any escaped bugs. |

---

### 🛠️ 4. Automation Standards
We use **Playwright (TypeScript)**. To keep our "10-Minute Rule" alive:
* **Atomic Tests:** One test, one assertion.
* **No Hard Waits:** Use auto-waiting and web-first assertions.
* **Data Independent:** Use API mocks or dynamic data seeding; never rely on static database state.

---

### 🗣️ 5. Communication & "The Rude Rule"
At Sky/TCS, we are partners with Developers, not police. 
* **Instead of:** "This is broken, fix it."
* **Try:** "I noticed the MFA token expires in 10 seconds instead of 60. Is that expected behavior according to the security spec?"
* **RCA Spirit:** If a bug reaches production, we ask **"What failed in our process?"** never **"Who missed this?"**

---

### 🏁 Your Success Metric
You are successful here if, by the end of Month 1, you can manage a **High-Risk feature release** independently using the tools in this repository.

> **Next Step:** Book a 15-minute 1-on-1 with the Lead QA Consultant to review your **[Engineering Skills Matrix](./SKILLS_MATRIX.md)**.
