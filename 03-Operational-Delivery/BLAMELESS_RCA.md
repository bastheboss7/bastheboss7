# 🔍 Blameless Root Cause Analysis (RCA)
## Culture: Learning Over Blame

**Core Principle:** Incidents are opportunities to improve systems, not opportunities to blame people.  
Every incident has multiple contributing factors—fix the system, not the person.

---

## When to Trigger RCA

✅ **Production incidents** with customer impact  
✅ **Critical test failures** that slipped through (escaped defects)  
✅ **Automation gaps** discovered in production  
✅ **Manual testing oversights** (exploratory blindspots)  
✅ **Process breakdowns** (Three Amigos skipped, RBT not followed)  
✅ **Near-misses** (almost-failures caught in UAT)  

---

## Example: Dark Mode Login Failure

**What Happened?** Login failed for Dark Mode users on Safari—critical path broken for 2% of users.  
**Impact:** 45-minute outage, customer frustration, media coverage risk.  

---

## RCA Process (The 5-Whys, Systems-Focused)

| Question | Answer | Root Cause Category |
|----------|--------|---------------------|
| **Why did login fail?** | CSS layer overlapped the Sign-In button | Technical defect |
| **Why wasn't this caught in testing?** | Playwright tests only ran in Light Mode | Automation strategy gap |
| **Why wasn't Dark Mode tested?** | Risk assessment (RBT matrix) missed UI theming | Missing exploratory context |
| **Why wasn't Dark Mode considered high-risk?** | "UI enhancement" label—not flagged as critical path | Risk classification error |
| **Why did we misclassify the risk?** | No manual exploratory testing for theme variations | Manual testing gap |

---

## Gen AI-Assisted RCA (Accelerator)

**How Gen AI enhances the RCA process:**

- **Automated Failure Analysis:** AI ingests logs, stack traces, and test output; identifies patterns and suggests root causes
- **Intelligent Triage:** LLM auto-classifies incidents (automation gap vs. manual gap vs. process gap)
- **RCA Summarization:** Gen AI drafts initial RCA document with 5-Whys chain; humans validate/refine
- **Corrective Action Suggestions:** AI proposes preventive measures based on historical incident patterns

**Example:**
> **AI Summary:** "Dark Mode CSS layer issue. Playwright tests insufficient (Light Mode only). Exploratory testing guidance was missing. RBT matrix didn't account for visual variations. Suggest: Add Dark Mode to config, train exploratory testers, add visual accessibility to RBT."

**Human Step:** Review AI analysis, validate root causes, confirm corrective actions align with team values.

*Note: Gen AI accelerates analysis; humans ensure blameless, learning-focused culture.*

---

## Key Insights (Not Blame)

🔴 **Automation Alone Failed:** Playwright regression only covered Light Mode  
🔴 **Manual Gap:** Exploratory testers weren't briefed on Dark Mode risks  
🔴 **Strategy Gap:** RBT matrix didn't account for visual/theme variations  
🔴 **Process Gap:** Three Amigos meeting didn't discuss "theme combinations"  

**None of these are "someone's fault"—they're system improvements.**

---

## Corrective Actions (Process, Not People)

### Immediate (24 hours)
- [ ] **Automation:** Add Dark Mode to Playwright test `config` (10% of regression runs)
- [ ] **Manual:** Brief team on visual regression scenarios (theme × browser × device)

### Structural (Next sprint)
- [ ] **RBT Update:** Add "Visual & Theme Combinations" to critical path assessment
- [ ] **Three Amigos:** Add "Theme/Accessibility Verification" checklist item
- [ ] **Exploratory Testing:** Train team on theme/contrast edge cases (user accessibility)

### Long-term (1-3 months)
- [ ] **Visual Regression Tool:** Implement automated visual diffing (Playwright/Percy)
- [ ] **Manual Training:** Workshop on accessibility-first testing (Dark Mode, WCAG compliance)
- [ ] **RBT Refinement:** Include "Visual Accessibility" as core risk dimension

---

## Blameless RCA Meeting Notes

**Attendees:** Dev lead, QA lead, Product manager, Automation engineer, Manual testers  
**Tone:** Curiosity, not judgment. "Why did we miss this?" not "Who screwed up?"  

**Conversation:**
- ✅ "Playwright strategy was good for happy path, but visibility needed expansion."
- ✅ "Exploratory testing could have caught this with right guidance."
- ✅ "RBT missed a category—UI theming is now flagged as critical."
- ❌ Don't say: "QA should have found this."
- ❌ Don't say: "The tester wasn't thorough."
- ❌ Don't say: "We need to blame someone."

---

## Why This Matters

💡 **Blameless RCA = Better Systems**  
- Teams speak up about issues (no fear of punishment)
- Root causes get addressed (not superficial blame)
- Learning spreads across team (everyone benefits)
- Automation + manual testing both improve together

💡 **Blame-Based RCA = Worse Outcomes**  
- Teams hide near-misses (to avoid blame)
- Same mistakes repeat (root causes ignored)
- Culture of fear (people protect themselves)
- Automation and manual testers blame each other