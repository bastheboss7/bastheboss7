# 🤝 Team Onboarding: The High-Trust QA Way
> **Welcome to the Team!** This guide defines our "Triangle of Quality": balancing Human Intuition, Automated Guardrails, and AI Acceleration.

---

### 1. ⚖️ The Triangle of Quality (Your Daily Balance)
We maintain a 5:1 Dev-to-QA ratio by distributing effort equally across three pillars:

| Pillar | Focus Area | Your Tooling |
| :--- | :--- | :--- |
| **🧠 Manual** | **Exploratory & UX:** Find what the requirements missed. | Session-Based Charters, Persona Testing. |
| **🤖 Automation** | **Regression & Speed:** Protect the "Golden Paths." | Playwright (TS), API Integration, CI/CD. |
| **✨ AI-Augmented** | **Productivity & Analysis:** Speed up the boring stuff. | GitHub Copilot, ChatGPT (Test Data/BPMN). |

---

### 2. 🛠️ Execution Standards: The Three Pillars

#### 🧠 Manual Excellence (Exploratory Charters)
We don't do "Step-by-Step" manual scripts. We use **Exploratory Charters**:
* **Time-Boxed Sessions:** 60-90 minutes of focused "destructive" testing.
* **Persona-Driven:** Testing as a "New User" vs. an "Admin" vs. a "Hacker."
* **Documentation:** Use Loom or screenshots; focus on *observability* rather than long-form writing.

#### 🤖 Automation Standards (Playwright/TypeScript)
We follow the "10-Minute Rule": Our smoke suite must finish in 10 minutes.
* **Atomic Tests:** One test, one assertion. No "Flaky" logic.
* **Shift-Left:** We write the "Skeleton" of the automation *before* the Dev finishes the code.
* **API First:** If you can test it with an API call (Gate 2), don't do it via the UI.

#### ✨ AI Integration (Augmented QA)
We expect you to use AI to 10x your output.
* **Test Data:** Use LLMs to generate complex JSON payloads or edge-case boundary data.
* **Boilerplate:** Use Copilot to generate Page Objects and repetitive Playwright selectors.
* **Log Analysis:** Use AI to parse large Splunk/Datadog logs to find the "needle in the haystack" during RCAs.

---

### 🔄 3. The Sprint Workflow (10-Day Cycle)



| Days | Phase | Manual Focus | Automation Focus | AI Focus |
| :--- | :--- | :--- | :--- | :--- |
| **1-2** | Refinement | Logic "Sniff Test" | Testability Audit | BDD/Gherkin Drafting |
| **3-5** | Skeleton | Charter Planning | Page Object creation | Mock Data Generation |
| **6-8** | Execution | **Exploratory Testing** | Script Execution | Log/Error Analysis |
| **9-10** | Hardening | Edge-case validation | Refactoring scripts | RCA Summarization |

---

### 🗣️ 4. Communication: The "Consultant" Voice
At Sky/TCS, we are partners. 
* **Instead of:** "This is broken."
* **Try:** "I explored the MFA flow with a 3G network simulation and found a timeout issue. Should we adjust the threshold for mobile users?"
* **AI Ethics:** Never paste client-sensitive PII into public AI tools. Always use sanitized data.

---

### 🏁 Your Success Metric
You are successful here if you can deliver a **Critical Feature** by Month 1 using the **"Power of Three"**: 
1. An **Automation Suite** that passes in CI. 
2. A **Manual Charter Report** detailing found edge cases. 
3. An **AI-Driven Data Set** that covers 100+ scenarios.

> **Next Step:** Book a 15-minute 1-on-1 with the Lead QA Consultant to review your **[Engineering Skills Matrix](./SKILLS_MATRIX.md)**.
