# 🤝 Three Amigos Refinement Checklist
## Pre-Development Quality Gate (Definition of Ready)

**When:** Sprint Planning or before development begins  
**Who:** Product Owner (What), Developer (How), QA/Tester (Verify)  
**Goal:** Ensure shared understanding before building. Catch ambiguity early—it's cheaper than fixing it later.

---

## Story Clarity
- [ ] **Acceptance Criteria:** Clear, testable statements (not vague wishes)  
  - ✅ "User can reset password via email link"  
  - ❌ "Password reset works well"
- [ ] **Happy Path:** What's the ideal user journey?  
- [ ] **Edge Cases:** Defined behavior for errors (invalid email, expired token, locked account)
- [ ] **Scope:** What's IN this story? What's explicitly OUT?

## Testing Strategy
- [ ] **Manual First:** Where does human judgment matter? (UX, security-sensitive paths, user frustration)
- [ ] **Automation Second:** What repeats daily in regression? (Happy path, data validation)
- [ ] **Test Data:** Do we have accounts/scenarios to test all paths?
- [ ] **Localization:** Does this need testing in multiple regions/languages?

## Technical Feasibility
- [ ] **Architecture Review:** Can testers interact with this UI/API? Are selectors stable?
- [ ] **Performance Requirements:** Response time SLAs? Load expectations?
- [ ] **Observability:** What logs/events confirm success? How do we detect failures?
- [ ] **Security Check:** Any sensitive data flows? Authentication/authorization needs?

## Acceptance & Definition of Done
- [ ] **DoD Criteria Met:** Code review, unit tests, documentation (before QA)
- [ ] **Deployment Plan:** How does this ship? Any database changes? Rollback plan?
- [ ] **Success Metrics:** How do we measure if this feature works (for users, not just QA)?

## Risk Assessment
- [ ] **Complexity:** Low / Medium / High?
- [ ] **Risk Areas:** What could go wrong? (Integration, security, performance)
- [ ] **Blockers:** Dependencies on other teams/systems?
- [ ] **Assumptions:** What are we assuming to be true? (3rd party APIs available, data consistency, etc.)

## Gen AI-Assisted Refinement (Optional Accelerator)
- [ ] **Gen AI Test Scenarios:** Use LLM to auto-generate Gherkin scenarios from acceptance criteria as a starting point
- [ ] **AI-Suggested Edge Cases:** Have Gen AI identify potential edge cases; validate with team judgment
- [ ] **Test Data Generation:** Request Gen AI to suggest synthetic test data (user personas, payloads); verify realistic coverage
- [ ] **Verification:** Human testers review AI-generated scenarios for accuracy before commitment

*Note: Gen AI is a brainstorming tool, not a decision-maker. All AI-generated content must pass team judgment.*

---

## Sign-Off
**Product:** ________________  **Date:** _____  
**Developer:** ________________  **Date:** _____  
**QA/Tester:** ________________  **Date:** _____  

*By signing, each role confirms they understand the story and can commit to their part.*

---

## Key Principles

📌 **Questions over Assumptions:** If you're unsure, ask now—not during testing.  
📌 **Manual & Automation Balance:** Decide this together; don't leave QA to figure it out alone.  
📌 **One Definition of Ready:** If a story doesn't meet DoR, it doesn't move to dev—discuss refinement instead.