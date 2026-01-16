# 🤖 GenAI Prompt Engineering Templates for QA

> **Purpose:** Provide reusable prompt templates for leveraging GenAI in test design, defect analysis, and data generation. Use these as starting points to accelerate and standardize GenAI-driven QA activities.

---

## 1. Test Scenario Generation

**Prompt:**
```
You are a senior QA engineer. Generate comprehensive test scenarios for the following feature:

Feature Description: [Paste user story or feature details here]

Requirements:
- Include 2-3 happy path scenarios
- Include 5-7 negative and edge cases
- Use Gherkin (Given/When/Then) format
- Highlight accessibility and security considerations
```

---

## 2. Defect Root Cause Analysis (RCA)

**Prompt:**
```
You are an expert QA analyst. Analyze the following defect report and suggest:
1. Root cause(s)
2. Suggested fix
3. Additional edge cases to test
4. Security implications

Defect Details:
[Paste defect summary, logs, and relevant code snippets]
```

---

## 3. Synthetic Test Data Generation

**Prompt:**
```
You are a QA automation engineer. Generate 10 realistic test data payloads for the following API:

API Schema/Fields: [Paste schema or field list]

Requirements:
- 5 valid payloads (covering edge cases)
- 5 invalid payloads (missing fields, wrong types, boundary violations)
- Output as JSON
```

---

## 4. Exploratory Testing Charter Suggestions

**Prompt:**
```
You are a QA lead. Suggest exploratory testing charters for the following feature:

Feature Description: [Paste feature details]

Requirements:
- Focus on user empathy, usability, and edge cases
- Include time-box and personas to use
```

---

## 5. Automation Code Boilerplate Generation

**Prompt:**
```
You are a test automation architect. Generate a boilerplate [Playwright/Selenium/Appium] test for the following scenario:

Scenario: [Paste Gherkin scenario or test case]

Requirements:
```


## 6. Automation Code Review

**Prompt:**
```
You are a senior automation engineer. Review the following test automation code for quality, maintainability, and best practices.

Code:
[Paste code snippet here]

Requirements:
- Identify code smells, anti-patterns, or flaky logic
- Suggest improvements for readability, reliability, and performance
- Check for adherence to framework standards (naming, structure, error handling)
- Recommend enhancements for reporting, logging, and parallel execution
```

---

## 7. Dependency & Vulnerability Analysis

**Prompt:**
```
You are a principal software architect with expertise in dependency management and security. Analyze the following dependency file and provide a detailed report.

Dependency File (`[pom.xml/package.json/build.gradle]`):
```
[Paste the full content of your dependency file here]
```

Report Requirements:
1.  **Outdated Dependencies:** Identify all libraries that are not on the latest stable or LTS version. For each, specify the current version and the recommended version.
2.  **Known Vulnerabilities:** Cross-reference the libraries and their versions against a vulnerability database (like CVE or Snyk). List any dependencies with known security risks, their severity (Critical/High/Medium/Low), and a link to the vulnerability report.
3.  **Deprecated Libraries:** Flag any dependencies that are no longer maintained or have been deprecated. Suggest modern, actively maintained alternatives.
4.  **Summary:** Provide a high-level summary of the repository's dependency health and prioritize the top 3 most critical actions to take.
```

---

## 8. Automated Code Migration & Refactoring

**Prompt:**
```
You are a senior software engineer specializing in large-scale code migrations. You will be given a code snippet that uses an older version of a library and your task is to refactor it to use the new version.

**Migration Context:**
- **Library:** [e.g., Rest-Assured]
- **From Version:** [e.g., 4.5.1]
- **To Version:** [e.g., 5.3.0]
- **Key Breaking Changes:** [e.g., "The `given()` method is now static. `JsonPath` configuration has been moved to `JsonPathConfig`."]

**Original Code:**
```java
[Paste the original Java/TypeScript/etc. code snippet here]
```

**Task:**
1.  Refactor the code to be compatible with the new library version, applying the specified breaking changes.
2.  Ensure the refactored code maintains the original logic and functionality.
3.  Add comments to the new code explaining *what* was changed and *why*, referencing the breaking changes.
4.  List any other potential improvements related to performance or best practices in the new version.
```

---

*Tip: Always review and validate GenAI outputs before use in production. Human judgment is essential!*

*Last updated: January 2026*
