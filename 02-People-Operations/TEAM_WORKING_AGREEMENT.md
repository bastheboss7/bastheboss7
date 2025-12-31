# 🤝 Team Working Agreement (TWA)
> **Version:** 1.0  
> **Mission:** To maintain a 5:1 Dev-to-QA ratio through radical transparency, technical excellence, and shared accountability.

---

## 💎 1. Core Values: The "How We Lead"
Our culture is built on three non-negotiable pillars that allow us to scale quality without micromanagement.

### 🔴 Radical Candor
* **Challenge Directly, Care Personally:** We speak up early if a deadline is at risk. There are no "bad news" penalties.
* **Greenmelon Prevention:** We value a "Red" status reported early over a "Green" status that hides a disaster.

### 🗽 Empowerment & Autonomy
* **The "What" vs. The "How":** Leads define the 'What' (Business Value) and 'Why' (Risk). The Engineer defines the 'How' (Technical Implementation).
* **Stop-the-Line Authority:** Every QA Engineer is empowered to veto a release if a [Quality Gate](../01-Strategic-Governance/QUALITY_GATES.md) is breached.

### 📈 Objective Growth (Skills Matrix)
* **Competency-Based Trust:** Autonomy is linked to the [Skills Matrix](./SKILLS_MATRIX.md). As you level up, your decision-making authority increases.

---

## 🛠️ 2. Operational Standards

### 🛡️ The "Three Amigos" Protocol
No ticket moves to "In Progress" until a Developer, Tester, and Product Owner have agreed on:
1.  **Gherkin Acceptance Criteria** (Success).
2.  **RBT Score** (Risk).
3.  **Testability** (Can we automate this?).

### 🤖 Automation-First Mindset
* **Skeleton Phase:** Automation "skeletons" (Page Objects/Mocks) must be written *before* the Dev finishes the UI.
* **The 10-Minute Rule:** If the smoke suite takes longer than 10 minutes, we refactor or prune.

### 🧠 Manual Exploratory Standard
* Manual testing is reserved for **High-Value Discovery**, not repetitive checking. 
* All manual sessions must have a **Charter** and a **Time-box** (60-90 mins).

---

## 🔄 3. Communication & Feedback

| Event | Protocol | Goal |
| :--- | :--- | :--- |
| **Daily Stand-up** | Focus on Blockers and "Red" flags, not just "What I did." | Risk Mitigation. |
| **Pull Requests** | QA reviews Dev Unit Tests; Dev reviews QA Automation. | Cross-Skilling. |
| **Post-Mortems** | [Blameless RCAs](../03-Operational-Delivery/BLAMELESS_RCA.md) only. We fix the process, not the person. | Continuous Improvement. |

---

## ⚖️ 4. Conflict Resolution
If the team cannot agree on a "Release/No-Release" decision:
1.  Consult the **[RBT Priority Matrix](../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md)**.
2.  Review the **[Quality Gates](../01-Strategic-Governance/QUALITY_GATES.md)**.
3.  If the score is **Critical (15-25)** and gates are failing, the Lead QA has final Veto Power.

---

## 🏁 Agreement
By joining this squad, we commit to these standards to ensure we ship high-quality software at **Sky-speed** without burnout.
