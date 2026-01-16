# 🤖 Case Study: GenAI-Augmented Test Design
> **Objective:** Reducing the "Requirement-to-Test" lifecycle by 80% using LLM orchestration.

### 📋 The Problem
In high-velocity environments (like the **Gmail Authentication** module), manual test case design is often the slowest phase. For every new security feature:
1. QAs spend **2-4 hours** reading Product Requirement Documents (PRDs).
2. Manually drafting Gherkin scenarios.
3. Manually mapping scenarios to existing automation Page Objects.

### 💡 The Solution: The 'Shift-Left' AI Utility
I architected a workflow using **GPT-4o/Gemini Pro** to act as a "Co-Pilot" for the manual QA team.



#### The Workflow:
1. **Extraction:** The utility pulls the raw User Story from Jira.
2. **Synthesis:** A custom "System Prompt" instructs the AI to generate:
   - Positive/Negative test scenarios.
   - Boundary value analysis for fields (e.g., Gmail password length).
   - Compliance checks (MFA/GDPR).
3. **Drafting:** The AI outputs structured Gherkin (`.feature` files) and initial Playwright locators.
4. **Human-in-the-Loop:** The QA Lead (me) reviews and approves the logic, ensuring **Knowledge Sovereignty**.

### 📈 Measurable Impact

| Metric | Before AI | After AI | Improvement |
| :--- | :--- | :--- | :--- |
| **Test Case Design Time** | 180 Minutes | 15 Minutes | **91% Reduction** |
| **Automation Boilerplate** | 60 Minutes | 5 Minutes | **92% Reduction** |
| **Edge Case Discovery** | Manual/Human | AI-Suggested | **40% More Scenarios** |

### 🛠️ Tech Stack Used
- **Orchestration:** Node.js / Python
- **LLM:** OpenAI API (GPT-4o) / LangChain
- **Integration:** Jira REST API
- **Framework:** Playwright (TypeScript)

---

### 🧠 Leadership Philosophy: "Augmentation, Not Replacement"
A key part of my leadership was addressing the "Emotional Side" of AI. 
- I held workshops to show the team that AI handles the **boring repetitive tasks**, allowing them to focus on **Creative Exploratory Testing**. 
- This increased team morale and transformed "Manual Testers" into "AI-Assisted Quality Engineers."
