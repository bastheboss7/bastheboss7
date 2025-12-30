# ⚡ Tiered Quality Gates: Balancing Velocity & Safety
> **Concept:** Tailoring the governance depth to the release type to eliminate "Gate Bypassing."

To prevent the team from continuously hitting the **Emergency Override Protocol**, we implement **Tiered Gates**. This ensures that even the fastest "Hotfix" undergoes automated validation.

---

### 🚦 The Three Lanes of Quality

| Lane | Release Type | Gate Depth | Targeted Execution Time |
| :--- | :---: | :--- | :---: |
| **🔴 FAST LANE** | Critical Hotfix (P0) | **Smoke & Core API:** Only critical path (Login/Pay) + Unit Tests. | **< 5 Minutes** |
| **🟡 STANDARD LANE**| Weekly Sprint Release | **Full Functional:** All new features + P1/P2 Regression. | **< 15 Minutes** |
| **🔵 DEEP LANE** | Major Monthly Release| **Full Regression + NFT:** Security, A11y, and Performance. | **< 60 Minutes** |

---

### 🛠️ Execution Logic

#### 1. The Fast Lane (Hotfixes)
* **Goal:** Stop the bleeding without making it worse.
* **Automation:** Trigger a specific Playwright/Appium tag `@CriticalSmoke`.
* **Manual:** Peer Review of the code change + 1-device "Happy Path" check.

#### 2. The Standard Lane (The Sprint Work)
* **Goal:** Maintain stable velocity.
* **Automation:** Full suite of `@Regression` + `@NewFeature` tags.
* **Governance:** Requires 100% pass on all "High Risk" items as per the [RBT Matrix](./RBT_PRIORITY_MATRIX.md).

#### 3. The Deep Lane (The "Hardening" Cycle)
* **Goal:** Total system integrity.
* **Execution:** Run overnight or on a dedicated weekend environment.
* **Scope:** Full End-to-End, Cross-Browser (Mobile/Tablet/Web), and Penetration Testing.

---

### 🧠 Why this solves the "Override" Problem:
By creating the **Fast Lane**, we remove the *excuse* to bypass the gates. 
* If a fix is "Emergency," we don't skip the gate—we use the **Fast Lane Gate**.
* This keeps the **Audit Trail** clean.
* It ensures that even in a P0 crisis, the "Login" flow is automatically verified before the code reaches the customer.

---

### 🗣️ Leadership Narrative
> "In my experience, teams bypass gates because the gates are too heavy for the task at hand. By implementing **Tiered Gates**, I provide the business with the agility it needs for hotfixes while maintaining the rigorous safety standards required for major releases. We move as fast as the risk allows."
