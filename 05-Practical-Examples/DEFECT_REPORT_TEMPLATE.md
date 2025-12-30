# 🐛 Defect Report Template
## With Gen AI-Enhanced Root Cause Analysis

---

## Standard Defect Report Structure

### **Defect ID:** `DEF-2025-001`  
### **Priority:** 🔴 Critical / 🟠 High / 🟡 Medium / 🟢 Low  
### **Severity:** 🔴 Blocker / 🟠 Major / 🟡 Minor / 🟢 Trivial  
### **Status:** New / In Progress / Fixed / Retest / Closed  
### **Reported By:** [QA Tester Name]  
### **Assigned To:** [Developer Name]  
### **Found In:** Version 2.5.0 / Sprint 23  
### **Environment:** Production / Staging / QA / Local  

---

## 📋 Summary
**One-line description of the defect:**  
Example: "User cannot reset password when email contains special characters (+, .)"

---

## 📝 Description

### What Happened?
Provide a clear, detailed description of the defect.

**Example:**
> When a user attempts to reset their password using an email address containing special characters (e.g., `user+test@example.com`), the system rejects the request with a "400 Bad Request" error. The user receives a generic error message: "Something went wrong. Please try again later."

### Expected Behavior
What should happen according to requirements?

**Example:**
> The system should accept valid email addresses (RFC 5322 compliant), including those with `+` symbols, and send a password reset email successfully.

### Actual Behavior
What actually happens?

**Example:**
> The system returns a 400 error. No reset email is sent. The user is stuck and cannot recover their account.

---

## 🔁 Steps to Reproduce

1. Navigate to `https://app.example.com/forgot-password`
2. Enter email: `user+test@example.com`
3. Click "Send Reset Email" button
4. Observe the error message
5. Check server logs (see 400 Bad Request in backend)

**Reproducibility:** 100% reproducible (occurs every time)  
**Browsers Tested:** Chrome 120, Firefox 121, Safari 17  
**Devices Tested:** Desktop (macOS), Mobile (iOS 17)  

---

## 🖼️ Evidence

### Screenshots
- [Attach screenshot of error message]
- [Attach screenshot of network tab showing 400 error]

### Video Recording
- [Link to Loom/screen recording showing reproduction steps]

### Logs
```
[2025-12-30 10:23:45] ERROR: Invalid email format: user+test@example.com
[2025-12-30 10:23:45] Backend Response: 400 Bad Request
[2025-12-30 10:23:45] Validation regex failed: ^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$
```

---

## 🔍 Root Cause Analysis (Manual)

### Initial Investigation
**Backend Validation:** The email validation regex does not include `+` as a valid character, despite it being RFC 5322 compliant.

**Code Location:** `src/validators/emailValidator.ts` (Line 42)

**Current Regex:**
```regex
^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$
```

**Issue:** Missing `+` character in allowed email prefix characters.

### Suggested Fix
Update regex to include `+`:
```regex
^[a-zA-Z0-9._+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

---

## 🤖 Gen AI-Assisted RCA (Accelerator)

### AI Analysis Request
**Prompt to LLM:**
> Analyze the following defect report and suggest root causes:
> 
> **Issue:** Email validation fails for addresses with `+` symbol  
> **Current Regex:** `^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$`  
> **Error:** 400 Bad Request when user enters `user+test@example.com`  
> 
> Provide:
> 1. Root cause analysis
> 2. Suggested regex fix
> 3. Additional edge cases to test
> 4. Security implications

### AI-Generated Response

**Root Cause:**
> The email validation regex does not comply with RFC 5322, which permits special characters including `+`, `!`, `#`, `$`, `%`, `&`, `'`, `*`, `/`, `=`, `?`, `^`, `` ` ``, `{`, `|`, `}`, and `~` in the local part of an email address.
> 
> The current regex explicitly excludes these characters, causing valid email addresses to be rejected. This is a **validation logic error**, likely introduced to prevent injection attacks but overly restrictive.

**Suggested Fix:**
```regex
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```
> This regex includes `+` and `%` (common in Gmail and other providers) while maintaining reasonable security constraints.

**Additional Edge Cases to Test:**
1. `user.name+tag@example.com` (period + plus)
2. `user%test@example.com` (percent symbol)
3. `user_name@example.co.uk` (multi-level TLD)
4. `user@subdomain.example.com` (subdomain)
5. `user..double@example.com` (consecutive dots - should FAIL)
6. `user@.example.com` (leading dot in domain - should FAIL)

**Security Implications:**
> **Concern:** Allowing `+` and other special characters increases the attack surface for email-based injection (e.g., SMTP header injection).
> 
> **Mitigation:** 
> - Sanitize email input before passing to email sending library
> - Use a well-tested email validation library (e.g., `validator.js`, `email-validator`)
> - Implement server-side rate limiting to prevent abuse
> - Log suspicious patterns (e.g., SQL keywords in email)

---

## ✅ Human Validation of AI Analysis

### QA Review:
✅ **Root cause confirmed:** Regex issue is accurate  
✅ **Suggested fix accepted:** Regex update is valid  
⚠️ **Security concern noted:** Will create separate ticket for injection testing  
✅ **Edge cases valuable:** Will add to regression suite  

### Additional Notes (Human Added):
- **Business Impact:** 2% of users use Gmail `+` aliasing (based on analytics)
- **User Feedback:** 3 support tickets logged in past week
- **Workaround:** Advise users to remove `+` temporarily (not ideal)

---

## 🛠️ Recommended Actions

### Immediate (Dev Team)
- [ ] Update email validation regex in `src/validators/emailValidator.ts`
- [ ] Add unit tests for special character emails
- [ ] Deploy fix to staging for QA validation

### Testing (QA Team)
- [ ] Retest with `user+test@example.com` after fix
- [ ] Execute AI-suggested edge cases (6 scenarios)
- [ ] Verify no other validation points reject special characters (API, frontend)
- [ ] Conduct security testing for injection vulnerabilities

### Long-term (Product Team)
- [ ] Review all validation logic for RFC 5322 compliance
- [ ] Replace custom regex with industry-standard library
- [ ] Add monitoring for validation failures (track rejected emails)

---

## 📊 Impact Assessment

| Dimension | Impact |
|-----------|--------|
| **User Impact** | 🔴 High - 2% of users blocked from password reset |
| **Business Impact** | 🟠 Medium - Support tickets increasing, frustration reported |
| **Technical Risk** | 🟡 Low - Fix is straightforward, low regression risk |
| **Security Risk** | 🟡 Medium - Requires injection testing post-fix |

---

## 🔗 Related Items

- **User Story:** `US-456` - Implement password reset flow
- **Similar Defects:** `DEF-2024-789` - Email validation failed for international domains
- **Knowledge Base:** RFC 5322 Email Compliance Guide (internal wiki)
- **Jira Epic:** `EPIC-123` - Authentication & Security Improvements

---

## 💬 Comments & Discussion

**Developer (2025-12-30):**  
> Thanks for the detailed report! The regex fix looks good. I'll also add tests for the edge cases suggested by the AI analysis. ETA: 2 hours.

**QA (2025-12-30):**  
> Confirmed. Will retest on staging tomorrow. Also creating a separate ticket for security injection testing (as suggested by AI).

**Product Manager (2025-12-30):**  
> Good catch. This explains the recent spike in support tickets. Prioritizing this for today's hotfix release.

---

## 🔑 Key Principles

### Effective Defect Reporting
✅ **Clear Summary:** One-line description that explains the issue  
✅ **Reproducible Steps:** Anyone should be able to recreate the issue  
✅ **Evidence:** Screenshots, videos, logs—proof of the problem  
✅ **Business Context:** Impact on users and business  

### Gen AI-Enhanced RCA
✅ **AI Accelerates Analysis:** LLMs identify root causes faster (from logs, code patterns)  
✅ **Human Validates AI:** QA reviews AI suggestions for accuracy  
✅ **AI Suggests Edge Cases:** Expand test coverage beyond initial discovery  
✅ **Security Awareness:** AI flags potential security implications  

### Collaboration Over Blame
✅ **Blameless Culture:** Focus on system improvement, not individual fault  
✅ **Transparent Communication:** Share findings, suggestions, and concerns openly  
✅ **Cross-Functional Input:** Dev, QA, Product, Security—all perspectives matter  

---

**Philosophy:** A great defect report saves hours of back-and-forth. Gen AI amplifies the analysis, but human judgment ensures quality and context.
