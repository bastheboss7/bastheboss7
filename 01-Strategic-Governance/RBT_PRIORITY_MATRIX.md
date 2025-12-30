# ⚖️ Risk-Based Testing (RBT) Matrix
> **Philosophy:** "Test what matters." Allocate manual testers where critical thinking wins, and automation where repeatability scales.

This matrix is the bridge between **business priorities** and **testing resources**. It answers: *What should we test manually vs. automate?*

## The Decision Framework

| Feature Area | Business Impact | Failure Risk | Risk Score | Testing Strategy |
| :--- | :---: | :---: | :---: | :--- |
| **Primary Login (Happy Path)** | 5 | 1 | 5 | **Automated (Sanity)** - Regression baseline |
| **MFA / 2FA Verification Flow** | 5 | 3 | 15 | **Manual + Automated** - Expert judgment + coverage |
| **Account Recovery (Lost Password)** | 4 | 4 | 16 | **Primary: Manual** - User empathy & edge cases first |
| **UI Localization (Labels/Links)** | 1 | 1 | 1 | **Manual Spot-Check** - Occasional human eye |
| **OAuth 3rd Party Integration** | 4 | 3 | 12 | **API Automation** - Contract validation + integration |

## Risk Score Strategy

- **Risk 15-25 (Critical):** Stop-ship issues. Pair manual exploratory testing with automated regression checks. Manual testers first.
- **Risk 8-14 (Medium):** Mix manual for new features + automation for regression. Balance required.
- **Risk 1-7 (Low):** Lighter touch. Automation-first, occasional manual verification.

## When Manual Testing Wins

✅ **Exploratory & Context-Driven:** Discovering unexpected flows (e.g., user cancels mid-MFA)  
✅ **Usability & UX:** Does the error message help users recover? (Automation can't judge this)  
✅ **Security-Sensitive Flows:** Authentication, data export, payment—human oversight reduces risk  
✅ **Visual & Localization:** Color, alignment, cultural appropriateness across regions  
✅ **User Empathy:** How would a frustrated user behave? Manual testers simulate real frustration  

## When Automation Wins

✅ **High-Frequency Regression:** Login > Profile > Settings > Logout (runs 100x/day safely)  
✅ **Data Validation:** API contracts, database consistency, performance SLAs  
✅ **Multi-Environment Testing:** Same test across staging, QA, and production-like environments  
✅ **CI/CD Gate:** Automated sanity before code ships to staging  
✅ **Load & Scale:** Testing with 1000s of concurrent users (humans can't do this)  

## Gen AI Multiplier Effects

**Gen AI enhances BOTH manual and automated testing decisions:**

### For Manual Testing (Higher Risk Areas)
- **Exploratory Guidance:** Gen AI suggests edge cases based on feature complexity and historical defect patterns
- **Test Data Generation:** Synthetic user personas and scenarios to inform exploratory test paths
- **Accessibility Insights:** AI flags potential UX/accessibility issues before manual testers investigate

### For Automation (High-Frequency Regression)
- **Test Case Generation:** LLMs auto-generate Gherkin scenarios from acceptance criteria (50% time savings)
- **Self-Healing:** AI-adaptive selectors and intelligent waits reduce flaky test failures by 40%
- **Intelligent Triage:** Auto-classify failures and suggest root causes before engineers investigate

### Risk-Based Gen AI Strategy
- **Risk 15-25 (Critical):** Use Gen AI to enrich manual exploratory guidance + auto-generate regression tests
- **Risk 8-14 (Medium):** Gen AI suggests test scenarios; manual testers validate; automation covers regression
- **Risk 1-7 (Low):** Gen AI-powered monitoring + lightweight automation; minimal manual effort

---
**Key Principle:** Automation accelerates regression. Manual testing accelerates discovery. **Gen AI accelerates both.**
- **Risk 1-4:** Minimal effort. Monitor via production logs/analytics.