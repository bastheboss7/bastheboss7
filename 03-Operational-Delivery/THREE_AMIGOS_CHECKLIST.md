# 🤝 Three Amigos Refinement Checklist

> **Purpose:** A pre-development quality gate to ensure shared understanding and catch ambiguity before a single line of code is written. It is the practical application of our "Shift-Left" philosophy.

-   **When:** During sprint planning or backlog refinement, before a story is moved to "In Progress."
-   **Who:** The Product Owner (defines the "what"), the Developer (defines the "how"), and the QA/Tester (defines the "verify").
-   **Goal:** To build a shared understanding of a feature, identify risks early, and ensure testability from the start.

---

## ✅ Checklist for "Definition of Ready"

### Story Clarity & Scope
- [ ] **Acceptance Criteria:** Are the criteria clear, concise, and testable? (e.g., "User can reset password via an email link" instead of "Password reset works well").
- [ ] **Happy Path:** Is the ideal user journey clearly defined?
- [ ] **Edge Cases & Sad Paths:** Have we defined the expected behavior for errors (e.g., invalid email, expired token, locked account)?
- [ ] **Scope:** What is explicitly IN this story, and what is OUT?

### Testing Strategy
- [ ] **Manual vs. Automation:** Have we agreed on what requires human judgment (e.g., UX, security) versus what should be automated (e.g., regression paths)?
- [ ] **Test Data:** Do we have the necessary accounts, data, and scenarios to test all defined paths?
- [ ] **Environment Needs:** Are there any specific environment or third-party dependencies required for testing?

### Technical Feasibility
- [ ] **Testability:** Can the UI and APIs be easily tested? Are locators stable and unique?
- [ ] **Observability:** What logs, events, or metrics will confirm that the feature is working as expected? How will we detect failures?
- [ ] **Security:** Does the feature handle sensitive data? Have we considered authentication and authorization requirements?

### Definition of Done
- [ ] **DoD Alignment:** Does the team agree on the criteria for the story to be considered "done" (e.g., code reviewed, unit tests passed, documentation updated)?
- [ ] **Deployment Plan:** How will this feature be deployed? Are there any database changes or rollback considerations?

### Gen AI-Assisted Refinement (Optional Accelerator)
- [ ] **AI-Generated Scenarios:** Have we used an LLM to generate initial Gherkin scenarios from the acceptance criteria to kickstart the discussion?
- [ ] **AI-Suggested Edge Cases:** Have we asked a Gen AI to identify potential edge cases that the team may have missed?
- [ ] **Verification:** Has a human tester reviewed all AI-generated content for accuracy and relevance before committing to it?

*Note: Gen AI is a powerful brainstorming tool, but it is not a replacement for human judgment. All AI-generated content must be validated by the team.*

---

## ✍️ Sign-Off

By signing below, each "amigo" confirms that they have a shared understanding of the story and are ready to commit to their respective roles.

-   **Product Owner:** ________________ (Date: _____)
-   **Developer:** ________________ (Date: _____)
-   **QA/Tester:** ________________ (Date: _____)

---

## 📌 Key Principles

-   **Questions Over Assumptions:** If you are unsure about something, ask now. It is always cheaper to clarify upfront than to fix a misunderstanding later.
-   **Shared Ownership of Quality:** The balance between manual and automated testing is a collective decision, not one left for QA to figure out alone.
-   **One Definition of Ready:** If a story does not meet the criteria in this checklist, it does not move into development. Instead, it is scheduled for further refinement.