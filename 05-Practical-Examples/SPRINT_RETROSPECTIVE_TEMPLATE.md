# 🔁 Sprint Retrospective Template
## Quality-Focused: What Worked, What Didn't, What's Next

---

## Sprint Overview

**Sprint Number:** 23  
**Sprint Goal:** Implement MFA feature and improve test automation coverage  
**Duration:** 2 weeks (Dec 16 - Dec 30, 2025)  
**Team:** 5 Developers, 3 QA, 1 Product Owner, 1 Scrum Master  

---

## 📊 Sprint Metrics

| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| **Stories Completed** | 8 | 7 | 🟡 87% |
| **Defects Found (Pre-Prod)** | N/A | 12 | ✅ Caught early |
| **Defects Escaped to Prod** | 0 | 1 | 🔴 Root cause needed |
| **Test Automation Coverage** | +10% | +12% | ✅ Exceeded |
| **Manual Test Execution Time** | 40 hrs | 35 hrs | ✅ Gen AI helped |
| **Sprint Velocity** | 34 pts | 31 pts | 🟡 Slightly below |

---

## ✅ What Went Well

### 1. Gen AI Test Design Acceleration
**What:** Used LLMs to generate Gherkin scenarios from user stories  
**Impact:** Reduced test design time by 50% (2 hours → 15 minutes per story)  
**Team Feedback:**  
> "The AI-generated edge cases for MFA were spot-on. We caught 3 defects in exploratory testing that we might have missed." - Alice (Senior QA)

**Action:** Continue Gen AI adoption; train mid-level QA on prompt engineering

---

### 2. Three Amigos Collaboration
**What:** Held Three Amigos sessions for all 7 user stories before sprint start  
**Impact:** Zero scope creep; clear acceptance criteria; fewer clarification questions  
**Team Feedback:**  
> "Having QA involved early helped us think about edge cases during design, not after implementation." - Dev Lead

**Action:** Make Three Amigos mandatory for all stories (add to Definition of Ready)

---

### 3. Blameless RCA for Production Defect
**What:** Conducted blameless RCA for escaped defect (email validation bug)  
**Impact:** Identified system gap (validation logic), not individual fault; team morale remained high  
**Team Feedback:**  
> "The Gen AI RCA summary saved us time. We focused on fixing the process, not blaming anyone." - Product Manager

**Action:** Continue blameless culture; use Gen AI for RCA acceleration

---

## ❌ What Didn't Go Well

### 1. Escaped Defect to Production
**What:** Email validation bug (`+` symbol rejection) reached production  
**Root Cause:** 
- Automation only covered happy path emails (no special characters)
- Manual testers didn't test Gmail `+` aliasing (assumed automation covered it)
- RBT matrix didn't flag email validation as high-risk

**Impact:** 3 customer support tickets; 2% of users affected  
**Action Items:**
- [ ] Update RBT matrix to include "Email Validation" as medium-risk
- [ ] Expand automated email test data (use Gen AI to generate edge cases)
- [ ] Add "Email Special Characters" to manual exploratory checklist

---

### 2. Flaky Automation Tests
**What:** 4 Playwright tests failed intermittently in CI/CD pipeline  
**Root Cause:** 
- Network latency in BrowserStack cloud
- Tests didn't use proper `waitForSelector` (implicit waits)
- No retry logic for known flaky scenarios

**Impact:** 6 false-positive failures; dev team frustrated; pipeline delays  
**Action Items:**
- [ ] Implement Gen AI self-healing (intelligent waits, adaptive selectors)
- [ ] Add retry logic (3 attempts) for network-dependent tests
- [ ] Review all Playwright tests for proper waits (pair programming with senior QA)

---

### 3. Manual Testing Bottleneck
**What:** Manual regression testing took 35 hours (even with Gen AI help)  
**Root Cause:** 
- 40% of test cases are still manual (complex UX flows, exploratory)
- Only 60% automation coverage for regression
- One manual tester was on leave (unplanned)

**Impact:** QA sign-off delayed by 1 day  
**Action Items:**
- [ ] Prioritize automation for top 10 most-executed manual tests (RBT-based)
- [ ] Cross-train developers to run smoke tests (shift-left)
- [ ] Build test execution resilience (coverage for leave/absences)

---

## 💡 Ideas & Experiments

### 1. Gen AI Exploratory Guidance (Experiment)
**Proposal:** Use Gen AI to suggest exploratory testing charters based on feature complexity  
**Expected Outcome:** Increase edge case discovery by 20%; reduce blind spots  
**Owner:** Alice (Senior QA)  
**Timeline:** Pilot in Sprint 24; review in Sprint 25 retro  

### 2. Visual Regression Testing
**Proposal:** Add Playwright + Percy for automated visual testing (Dark Mode, themes, responsiveness)  
**Expected Outcome:** Catch UI regression earlier (avoid Dark Mode incident repeat)  
**Owner:** Bob (Mid-Level QA)  
**Timeline:** Proof of concept in Sprint 24  

### 3. Shift-Left: Dev Smoke Tests
**Proposal:** Train developers to run 5-minute smoke test suite before PR submission  
**Expected Outcome:** Reduce QA rework; catch defects earlier  
**Owner:** Dev Lead + QA Lead  
**Timeline:** Training session in Sprint 24; mandatory by Sprint 25  

---

## 🎯 Action Items for Next Sprint

| Action | Owner | Priority | Due Date |
|--------|-------|----------|----------|
| Update RBT matrix (email validation risk) | QA Lead | 🔴 High | Sprint 24 Day 1 |
| Fix flaky Playwright tests (add waits) | Bob (QA) | 🔴 High | Sprint 24 Day 3 |
| Automate top 10 manual regression tests | Dev + QA Pair | 🟠 Medium | Sprint 24 End |
| Gen AI exploratory testing pilot | Alice (QA) | 🟡 Low | Sprint 24 End |
| Shift-left training for developers | Dev Lead | 🟠 Medium | Sprint 24 Day 5 |
| Visual regression POC (Playwright + Percy) | Bob (QA) | 🟡 Low | Sprint 25 |

---

## 📈 Quality Trends (Last 3 Sprints)

| Sprint | Escaped Defects | Pre-Prod Defects | Automation Coverage | Manual Hours |
|--------|-----------------|------------------|---------------------|--------------|
| **21** | 2 | 8 | 50% | 45 hrs |
| **22** | 1 | 10 | 58% | 42 hrs |
| **23** | 1 | 12 | 62% | 35 hrs |

**Observations:**
- ✅ **Pre-prod defect discovery improving** (8 → 10 → 12) - shift-left working
- ✅ **Automation coverage trending up** (50% → 62%) - good progress
- ✅ **Manual hours decreasing** (45 → 35) - Gen AI + automation helping
- 🔴 **Escaped defects stable at 1** - need to address root causes (RBT, coverage gaps)

---

## 🗣️ Team Feedback (Anonymous)

### What energized you this sprint?
- "Gen AI tools made test design fun and fast"
- "Blameless RCA felt safe—no finger-pointing"
- "Three Amigos sessions improved collaboration"

### What drained your energy?
- "Flaky tests are frustrating—feels like wasted effort"
- "Manual regression is repetitive—wish more was automated"
- "Production defect was stressful (even though not blamed)"

### One thing to improve next sprint?
- "Prioritize automation for high-frequency manual tests"
- "Fix flaky tests ASAP—they slow us down"
- "More training on Gen AI prompt engineering"

---

## 🎓 Team Shout-Outs

🏆 **Alice (Senior QA):** Led Gen AI pilot; generated edge cases that caught 3 defects  
🏆 **Dev Lead:** Supported Three Amigos adoption; improved BA-Dev-QA collaboration  
🏆 **Bob (Mid-Level QA):** Identified flaky test root cause; proposed visual regression POC  
🏆 **Product Manager:** Championed blameless RCA; kept team morale high during production incident  

---

## 🔑 Key Takeaways

### What Quality Means This Sprint
✅ **Shift-Left Success:** 12 defects caught pre-production (vs. 1 escaped)  
✅ **Gen AI Acceleration:** 50% faster test design; 35 hours of manual testing (down from 45)  
✅ **Blameless Culture:** Production incident handled constructively; no blame  
⚠️ **Coverage Gaps Remain:** Email validation edge cases missed; need RBT update  
⚠️ **Flaky Tests Erode Trust:** 6 false positives frustrate team; self-healing needed  

### Next Sprint Focus
1. **Fix Flaky Tests** - Priority #1 to restore pipeline confidence
2. **Automate Manual Bottlenecks** - Top 10 regression tests
3. **Strengthen RBT Matrix** - Include validation logic as medium-risk
4. **Experiment with Gen AI** - Exploratory charter generation pilot

---

**Retrospective Facilitator:** Scrum Master  
**Date:** December 30, 2025  
**Next Retro:** Sprint 24 (Jan 13, 2026)  

---

## 🔗 Resources

- [Sprint 23 Velocity Chart](link-to-jira-chart)
- [Defect Leakage Dashboard](link-to-dashboard)
- [Gen AI Test Design Guide](link-to-internal-doc)
- [Blameless RCA Report - DEF-2025-001](link-to-rca)

---

**Philosophy:** Retrospectives are about **continuous improvement**, not perfection. Every sprint reveals opportunities to strengthen quality, collaboration, and team morale. Embrace experiments, learn from failures, and celebrate wins—no matter how small.
