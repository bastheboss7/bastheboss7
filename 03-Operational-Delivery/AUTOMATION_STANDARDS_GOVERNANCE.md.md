# Unified Automation Code Review Checklist

## Core Global Standards

- **Test Isolation**
  - Each test must be independent and not rely on the state of other tests.
  - Shared resources (browsers, drivers, data) must be cleaned up after each test.
  - Use scenario/test-level setup and teardown hooks.

- **Clean Code**
  - Follow SOLID and DRY principles in all utility and page classes.
  - Use descriptive naming for classes, methods, and variables.
  - Remove dead code, unused imports, and commented-out blocks.
  - Maintain consistent code formatting and linting (e.g., Prettier, Checkstyle).

- **Data Seeding & Management**
  - Test data should be externalized (e.g., config files, Excel, JSON, ENV vars).
  - Avoid hardcoded values in test logic.
  - Use thread-safe or context-aware data loaders for parallel execution.

- **Configuration & Environment**
  - Centralize environment and test configuration (e.g., test.config.ts, ConfigManager).
  - Use environment variables for secrets and sensitive data.
  - Support for multiple environments (dev, qa, prod) must be present.

- **Reporting & Logging**
  - Use structured logging (e.g., Winston, SLF4J) with scenario/test context.
  - Integrate with reporting tools (ExtentReports, Allure, etc.).
  - Attach screenshots and logs on failure.

- **Parallelism & Thread Safety**
  - Use ThreadLocal or context-aware storage for drivers, loggers, and test data.
  - Ensure reporting and data utilities are safe for parallel execution.

- **Hooks & Lifecycle**
  - Use @Before, @After, @BeforeAll, @AfterAll (or Playwright fixtures) for setup/teardown.
  - Ensure global and scenario hooks are not misused for test logic.

- **Error Handling**
  - Catch and log exceptions with context.
  - Fail tests gracefully and provide actionable error messages.

- **Reusable Utilities**
  - Common utilities (browser, data, reporting) must be modular and reusable.
  - Avoid code duplication across stacks.

---

## Stack-Specific Addendums

### Playwright_BDD_Framework (Web, TypeScript)
- Use Playwright fixtures for browser/context/page isolation.
- Centralize browser management (see `BrowserManager.ts`).
- Use AsyncLocalStorage for per-test context in reporting/logging.
- All configuration in `test.config.ts` must support ENV overrides.
- Prefer TypeScript types and interfaces for models and test data.
- Use Cucumber steps and page objects for BDD alignment.

### WebBrowserAutomation_BDD_Framework (Web, Java, Selenium)
- Use ThreadLocal for WebDriver and ExtentTest instances.
- Hooks (`Hooks.java`) must manage browser and reporting lifecycle.
- Page Objects must extend a common base (e.g., `BasePageObject`).
- Use PageFactory for element initialization.
- Test data and config must be externalized (properties, Excel, etc.).
- Attach screenshots to Cucumber scenarios on failure.

### MobileAutomation_BDD_Framework (Mobile, Java)
- Use ThreadLocal for reporting and driver management.
- Centralize reporting via `ExtentReportManager.java`.
- Use annotation transformers for retry logic (e.g., `RetryTransformer`).
- Test data and config must be externalized and thread-safe.
- Ensure mobile-specific capabilities are configurable.

### evri-api-automation-framework (API, Java)
- Use thread-safe utilities for config and secrets (`PropertiesHandlers.java`).
- Centralize API client logic and logging.
- Data-driven tests should use external sources (Excel, JSON, etc.).
- Integrate structured logging and reporting for API requests/responses.
- Ensure parallel test execution does not leak state.

---


*This checklist is maintained by the Automation Lead and reflects unified governance across all automation stacks. Update as frameworks evolve.*

---

## Non-Conformance Protocol

If a Pull Request (PR) fails to meet any mandatory automation standard (e.g., the 'No Hard Wait' standard), it is automatically rejected. The PR rejection must include a link to the relevant Technical Standardization Policy for reference and remediation guidance.
