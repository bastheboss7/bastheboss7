# 🤝 Team Working Agreement (TWA)

> **Our Mission:** To build a high-trust, high-performance QA team that balances speed with quality, guided by principles of radical candor, empowerment, and objective growth.

This document outlines the shared behaviors and standards we commit to as a team. It is a living document, reviewed and updated quarterly.

---

## 💎 Core Values: The Foundation of Our Culture

Our culture is built on three non-negotiable pillars that enable us to scale quality effectively.

### Radical Candor
-   **Challenge Directly, Care Personally:** We provide feedback that is both kind and clear. We address issues early and constructively, without fear of blame.
-   **No "Green-Shifting":** We value a "Red" status reported early over a "Green" status that hides a potential disaster. Transparency is our default.

### Empowerment & Autonomy
-   **"What" vs. "How":** Leadership defines the "what" (business goals) and the "why" (risk context). Engineers are empowered to define the "how" (technical implementation).
-   **Stop-the-Line Authority:** Every QA Engineer has the authority to veto a release if a critical [Quality Gate](../01-Strategic-Governance/QUALITY_GATES.md) is breached, ensuring quality is never compromised.

### Objective Growth
-   **Competency-Based Trust:** Autonomy and responsibility are linked to the [Skills Matrix](./SKILLS_MATRIX.md). As team members level up, their decision-making authority expands.
-   **Continuous Improvement:** We are all committed to personal and professional growth, supported by mentorship and clear development plans.

---

## 🛠️ Operational Standards: How We Execute

### The "Three Amigos" Protocol
-   No ticket moves to "In Progress" until a Developer, Tester, and Product Owner have aligned on the acceptance criteria using the [Three Amigos Checklist](../03-Operational-Delivery/THREE_AMIGOS_CHECKLIST.md). This ensures shared understanding before any code is written.

### Automation-First Mindset
-   **Write Tests First:** Automation "skeletons" (e.g., Page Objects, API mocks) are created *before* the developer completes the UI, enabling parallel workstreams.
-   **The 10-Minute Rule:** If the primary regression suite takes longer than 10 minutes to run, we prioritize refactoring or pruning to maintain rapid feedback loops.

### High-Value Manual Testing
-   **Discovery, Not Repetition:** Manual testing is reserved for high-value discovery work, such as exploratory, usability, and security testing—not for repetitive checks.
-   **Chartered Sessions:** All manual testing sessions must have a clear **charter** defining the scope and goals, and be time-boxed (typically 60-90 minutes).

---

## 🔄 Communication & Feedback Loops

| Event | Protocol | Goal |
| :--- | :--- | :--- |
| **Daily Stand-up** | Focus on blockers and "Red" flags first, not just status updates. | Proactive Risk Mitigation. |
| **Pull Requests** | QA reviews developer unit tests; developers review QA automation code. | Shared Ownership & Cross-Skilling. |
| **Post-Mortems** | We conduct [Blameless RCAs](../03-Operational-Delivery/BLAMELESS_RCA.md) to fix the process, not to blame individuals. | Continuous System Improvement. |

---

## ⚖️ Conflict Resolution

If the team cannot reach a consensus on a "Release/No-Release" decision:
1.  **Consult the Data:** We first refer to the [RBT Priority Matrix](../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md) to assess the risk level.
2.  **Review the Gates:** We then check if any hard requirements from the [Quality Gates](../01-Strategic-Governance/QUALITY_GATES.md) have been missed.
3.  **Lead's Decision:** If the risk score is **Critical (15-25)** and a quality gate is failing, the QA Lead has the final veto power to ensure we protect our users.

---

## 🏁 Our Commitment

By joining this team, we all commit to upholding these standards. This agreement empowers us to ship high-quality software at a sustainable pace, fostering a culture of excellence and psychological safety.
