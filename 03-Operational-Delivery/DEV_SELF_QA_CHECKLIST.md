# 🛠️ Developer Self-QA Checklist (Low/Medium Risk Features)
> **Purpose:** To enable rapid delivery of low-risk features by shifting quality ownership to the engineering source.

When a feature is classified as **Tier 3 (Low Risk)** in our [RBT Matrix](../01-Strategic-Governance/RBT_PRIORITY_MATRIX.md), Developers must complete this checklist and attach evidence to the Jira ticket before moving it to "Done."

### 1. 🧪 Functional Verification
- [ ] **Positive Flow:** Does the feature work as described in the User Story?
- [ ] **UI Consistency:** Does the implementation match the Figma/Design spec (fonts, colors, spacing)?
- [ ] **Browser/Device Check:** Have you verified the change on at least one alternative browser (e.g., Safari if developing on Chrome)?

### 2. 🛡️ Safety & Resilience
- [ ] **Error Handling:** Does the app crash if you input invalid data or disconnect the internet?
- [ ] **Console Hygiene:** Are there any new errors or warnings appearing in the browser console?
- [ ] **Accessibility (A11y):** Have you run the 'Axe' or 'Wave' extension to check for basic contrast or ARIA label issues?

### 3. ⚙️ Automation & Logs
- [ ] **Unit Tests:** Have you updated/added unit tests to cover the new logic (Minimum 80% coverage)?
- [ ] **Observability:** Are the log messages clear? (Follows the **[Test Observability](../01-Strategic-Governance/QA_STRATEGY_ROADMAP.md)** pillar).
- [ ] **Integration:** Does the build pass in the CI/CD pipeline server?

---

### 🖇️ Evidence Requirements (The "Receipts")
To move a ticket to "Done" without formal QA intervention, the Developer must provide:
1. **Screenshot/Video:** A 10-second clip of the working UI flow.
2. **Logs/Network Tab:** Screenshot showing a successful 200 OK response for any new API calls.
3. **A11y Report:** A "Green" pass from the browser accessibility extension.

---

### 🧠 Leadership Note: "Why we do this"
This isn't "skipping QA." It is **Distributed Quality**. 
- It allows our **1 Manual Tester** to focus on complex exploratory testing of High-Risk security flows.
- It allows our **1 Automation Tester** to focus on building a robust, thread-safe framework.
- It empowers **Developers** to take pride in the "Definition of Done."
