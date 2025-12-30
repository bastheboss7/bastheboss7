# 📝 Test Scenario Templates
## Manual, Automation, and Gen AI-Enhanced Examples

---

## 🎯 Template 1: Manual Exploratory Testing

### Feature: User Account Recovery (High-Risk, Manual-First)

#### Context
**Business Impact:** 5/5 (Critical path)  
**Failure Risk:** 4/5 (Complex user flows)  
**Testing Approach:** Manual exploratory testing first; automate regression after validation

#### Exploratory Testing Charter
**Mission:** Explore account recovery flows to discover edge cases and usability issues that could frustrate users.

**Time-Box:** 90 minutes  
**Tester:** Senior QA (Level 3+)  
**Focus Areas:**
- User frustration points (error messages, recovery steps)
- Security edge cases (expired tokens, rate limiting)
- Cross-device/browser behavior inconsistencies

#### Manual Test Scenarios

**Scenario 1: Happy Path - Email Recovery**
```gherkin
Given the user has forgotten their password
When they click "Forgot Password"
And enter a valid registered email address
And click "Send Recovery Email"
Then they should receive an email within 2 minutes
And the email should contain a recovery link valid for 30 minutes
And clicking the link should allow password reset
And the new password should work for login
```

**Scenario 2: Edge Case - Expired Recovery Token**
```gherkin
Given the user received a password recovery email 31 minutes ago
When they click the recovery link
Then they should see "This link has expired" message
And the message should offer to resend the email
And the UI should remain accessible (no broken state)
```

**Scenario 3: Security - Multiple Recovery Attempts**
```gherkin
Given the user has requested 5 password resets in 10 minutes
When they attempt a 6th request
Then the system should show "Too many requests. Try again in 15 minutes"
And no new email should be sent
And the user's account should NOT be locked (avoid denial of service)
```

**Exploratory Notes:**
- ❓ What happens if user resets password on mobile, then tries old password on desktop?
- ❓ Does error message leak information (e.g., "This email doesn't exist" vs. generic message)?
- ❓ Can user navigate away mid-recovery and return later?
- ❓ Accessibility: Screen reader compatibility? Keyboard navigation?

---

## 🤖 Template 2: Automated Regression Testing

### Feature: Login Authentication (Low-Risk, Automation-First)

#### Context
**Business Impact:** 5/5 (Critical path)  
**Failure Risk:** 1/5 (Well-tested, stable)  
**Testing Approach:** Automate happy path + basic negatives; manual spot-check new changes

#### Playwright (TypeScript) Example

```typescript
import { test, expect } from '@playwright/test';

test.describe('Login Authentication - Regression Suite', () => {
  
  test('TC001: Valid login redirects to dashboard', async ({ page }) => {
    // Arrange
    await page.goto('https://app.example.com/login');
    
    // Act
    await page.fill('[data-testid="email"]', 'testuser@example.com');
    await page.fill('[data-testid="password"]', 'ValidPassword123!');
    await page.click('[data-testid="login-button"]');
    
    // Assert
    await expect(page).toHaveURL(/.*dashboard/);
    await expect(page.locator('[data-testid="welcome-message"]')).toContainText('Welcome back');
  });

  test('TC002: Invalid credentials show error', async ({ page }) => {
    // Arrange
    await page.goto('https://app.example.com/login');
    
    // Act
    await page.fill('[data-testid="email"]', 'invalid@example.com');
    await page.fill('[data-testid="password"]', 'WrongPassword');
    await page.click('[data-testid="login-button"]');
    
    // Assert
    await expect(page.locator('[data-testid="error-message"]'))
      .toContainText('Invalid email or password');
    await expect(page).toHaveURL(/.*login/); // Should remain on login page
  });

  test('TC003: Empty fields show validation error', async ({ page }) => {
    // Arrange
    await page.goto('https://app.example.com/login');
    
    // Act
    await page.click('[data-testid="login-button"]'); // Submit without filling
    
    // Assert
    await expect(page.locator('[data-testid="email-error"]')).toContainText('Email is required');
    await expect(page.locator('[data-testid="password-error"]')).toContainText('Password is required');
  });

});
```

#### BDD (Cucumber + Java) Example

```gherkin
Feature: Login Authentication

  Background:
    Given the user is on the login page

  Scenario: Successful login with valid credentials
    When the user enters email "testuser@example.com"
    And the user enters password "ValidPassword123!"
    And the user clicks the login button
    Then the user should be redirected to the dashboard
    And the welcome message should display "Welcome back"

  Scenario Outline: Login fails with invalid credentials
    When the user enters email "<email>"
    And the user enters password "<password>"
    And the user clicks the login button
    Then an error message should display "<error>"
    And the user should remain on the login page

    Examples:
      | email                  | password        | error                          |
      | invalid@example.com    | WrongPassword   | Invalid email or password      |
      | notregistered@test.com | AnyPassword123  | Invalid email or password      |
      | testuser@example.com   | ShortPwd        | Invalid email or password      |
```

---

## 🤖 Template 3: Gen AI-Enhanced Test Design

### Feature: Multi-Factor Authentication (MFA)

#### Gen AI Prompt for Test Scenario Generation

**Prompt to LLM:**
```
You are a senior QA engineer with expertise in security testing. Generate comprehensive test scenarios for a Multi-Factor Authentication (MFA) feature.

Context:
- Users receive a 6-digit code via SMS after entering valid credentials
- Code expires after 10 minutes
- Users have 3 attempts to enter correct code
- After 3 failed attempts, account is temporarily locked for 15 minutes

Generate:
1. Happy path scenarios (2-3)
2. Negative scenarios (5-7)
3. Edge cases related to timing, retries, and security
4. Accessibility and usability considerations

Output format: Gherkin (Given/When/Then)
```

#### AI-Generated Scenarios (Sample Output)

**AI Generated - Scenario 1: Happy Path**
```gherkin
Scenario: User successfully authenticates with MFA code
  Given the user has entered valid credentials
  And an MFA code has been sent to their registered phone number
  When the user enters the correct 6-digit code within 10 minutes
  Then the user should be authenticated
  And redirected to the dashboard
  And the MFA code should be invalidated for future use
```

**AI Generated - Scenario 2: Code Expiration**
```gherkin
Scenario: MFA code expires after 10 minutes
  Given the user received an MFA code 11 minutes ago
  When the user enters the code
  Then the system should display "Code expired. Request a new code."
  And the user should be able to request a new code
  And the old code should be permanently invalidated
```

**AI Generated - Scenario 3: Failed Attempts Leading to Lock**
```gherkin
Scenario: Account temporarily locked after 3 failed MFA attempts
  Given the user has entered valid credentials
  And an MFA code has been sent
  When the user enters an incorrect code 3 times
  Then the account should be locked for 15 minutes
  And a notification should be sent to the user's email
  And the system should display "Too many failed attempts. Try again in 15 minutes."
  And the user should not be able to request a new code during lockout
```

**AI Generated - Edge Case: Network Delay**
```gherkin
Scenario: User submits correct code during network latency
  Given the user received an MFA code 9 minutes and 30 seconds ago
  When the user enters the correct code
  And there is a 45-second network delay in submission
  Then the system should handle the delay gracefully
  And authenticate the user if total time < 10 minutes from generation
  Or reject with "Code expired" if total time > 10 minutes
```

#### Human Validation & Refinement

**QA Review Notes:**
✅ **Accepted:** Scenarios 1, 2, 3 - Accurate and comprehensive  
⚠️ **Modified:** Edge case (network delay) - Clarified timing calculation  
❌ **Rejected:** AI suggested "code reuse" scenario - already covered in Scenario 1  
➕ **Added by Human:** What if user never receives SMS? (carrier issue, wrong number)  

**Final Scenario (Human-Added):**
```gherkin
Scenario: User doesn't receive MFA code due to carrier issue
  Given the user has entered valid credentials
  And the MFA code was sent 2 minutes ago
  When the user clicks "I didn't receive a code"
  Then the system should offer to resend via SMS or alternate method (email)
  And log the delivery failure for monitoring
  And the previous code should be invalidated
```

---

## 📊 Template 4: API Contract Testing

### Feature: User Profile API (Automation + Gen AI Data)

#### Rest-Assured (Java) Example

```java
@Test
public void testGetUserProfile_ValidToken_Returns200() {
    given()
        .header("Authorization", "Bearer " + validToken)
        .when()
        .get("/api/v1/users/profile")
        .then()
        .statusCode(200)
        .body("email", equalTo("testuser@example.com"))
        .body("firstName", notNullValue())
        .body("createdAt", matchesPattern("\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}Z"));
}

@Test
public void testUpdateUserProfile_InvalidData_Returns400() {
    String invalidPayload = """
        {
          "firstName": "",
          "email": "not-an-email"
        }
        """;
    
    given()
        .header("Authorization", "Bearer " + validToken)
        .contentType("application/json")
        .body(invalidPayload)
        .when()
        .put("/api/v1/users/profile")
        .then()
        .statusCode(400)
        .body("errors", hasSize(2))
        .body("errors[0].field", anyOf(equalTo("firstName"), equalTo("email")));
}
```

#### Gen AI-Generated Test Data

**Prompt to LLM:**
```
Generate 10 realistic user profile JSON payloads for testing. Include:
- 5 valid payloads (diverse demographics, edge cases like long names)
- 5 invalid payloads (missing fields, wrong types, boundary violations)
```

**AI Output (Sample):**
```json
// Valid Payload 1
{
  "firstName": "María",
  "lastName": "García-López",
  "email": "maria.garcia@example.com",
  "phoneNumber": "+34612345678",
  "dateOfBirth": "1990-05-15"
}

// Invalid Payload 1 (Missing required field)
{
  "firstName": "John",
  "email": "john@example.com"
  // Missing lastName
}

// Invalid Payload 2 (Invalid email format)
{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "not-an-email",
  "phoneNumber": "+1234567890"
}
```

---

## 🔑 Key Principles

### Manual Testing
✅ Focus on usability, user empathy, and exploratory discovery  
✅ Document edge cases and assumptions for automation  
✅ Validate that error messages are helpful (not just technically correct)  

### Automation Testing
✅ Automate happy paths and high-frequency regression  
✅ Use data-driven tests for coverage (examples, parameterization)  
✅ Keep tests fast, stable, and maintainable (Page Object Model)  

### Gen AI-Enhanced Testing
✅ Use AI for brainstorming, not decision-making (always validate)  
✅ Review 100% of AI-generated test scenarios  
✅ Combine AI suggestions with human domain knowledge  
✅ Document AI limitations (e.g., doesn't understand business context)  

---

**Philosophy:** Templates accelerate productivity—but critical thinking ensures quality. Use these as starting points, not replacements for judgment.
