---
description: This file describes the testing guidelines for the project.
applyTo: "**/*"
---

# Testing and Quality Assurance Instructions

## 1. General Principles

- Follow a test-first development approach whenever practical.
- Apply Test-Driven Development (TDD) and Behavior-Driven Development (BDD).
- Write tests to verify correctness, reliability, security, and performance where relevant.
- Prefer automated tests over manual testing whenever practical.
- Treat tests as an integral part of implementation, not an afterthought.
- Ensure tests are isolated, repeatable, deterministic, and independent of execution order.
- Focus on observable behavior and expected outcomes rather than implementation details.
- Prioritize critical business logic, complex functionality, and high-risk components.
- Never weaken or remove tests simply to make an implementation pass.
- Never claim tests have passed unless they have actually been executed.

## 2. Test-Driven Development (TDD)

Follow the Red-Green-Refactor cycle.

### Red – Write a Failing Test

- Understand the requirements before implementing a solution.
- Identify expected behavior, acceptance criteria, and relevant edge cases.
- Write a focused test describing the expected behavior.
- Run the test and verify that it fails for the expected reason.
- Avoid implementing production code before establishing the failing test, except when initial project setup or exploratory work requires it.

### Green – Implement the Solution

- Write the minimum production code necessary to satisfy the failing test.
- Avoid unnecessary abstractions and premature optimization.
- Run the relevant tests and verify that they pass.
- Ensure existing tests remain successful.

### Refactor – Improve the Implementation

- Improve readability, structure, and maintainability without changing behavior.
- Remove duplication and unnecessary complexity.
- Keep the test suite passing throughout refactoring.
- Re-run relevant tests after refactoring.

Repeat this cycle for each independently testable requirement.

## 3. Behavior-Driven Development (BDD)

- Express requirements in terms of observable business behavior.
- Describe expected behavior from the perspective of users, stakeholders, or external systems.
- Use clear, domain-specific language understandable to technical and non-technical stakeholders.
- Structure scenarios using Given-When-Then whenever appropriate.

### BDD Scenario Structure

- **Given:** Describe the initial context or preconditions.
- **When:** Describe the action or event.
- **Then:** Describe the expected observable outcome.

Example:

```gherkin
Feature: User authentication

  Scenario: Successful login
    Given a registered user with valid credentials
    When the user submits the login form
    Then the user is authenticated
    And the user is redirected to the dashboard

  Scenario: Invalid credentials
    Given a registered user
    When the user submits an incorrect password
    Then authentication is rejected
    And a meaningful error message is displayed
```

- Cover successful workflows, validation failures, boundary conditions, and relevant exceptional scenarios.
- Avoid implementation-specific details in business-facing scenarios.
- Keep scenarios independent, focused, and reusable where appropriate.
- Translate acceptance criteria into executable tests whenever practical.

## 4. Testing Levels

Apply the appropriate testing levels based on architecture, requirements, and risk.

- **Unit Tests:** Verify individual functions, methods, components, and isolated business logic.
- **Integration Tests:** Verify interactions between modules, services, databases, APIs, and external dependencies.
- **End-to-End Tests:** Verify complete user workflows across the application.
- **Acceptance Tests:** Verify that implemented functionality satisfies business requirements and acceptance criteria.
- **Regression Tests:** Ensure existing functionality continues to work after changes.
- **Performance Tests:** Verify performance characteristics against relevant system requirements.
- **Security Tests:** Validate authentication, authorization, input validation, and protection against relevant vulnerabilities.

Prefer fast unit tests for frequent feedback and reserve slower integration and end-to-end tests for broader verification.

## 5. Test Structure and Organization

- Organize tests logically and consistently, typically mirroring the source code structure or established project conventions.
- Group related tests together.
- Use descriptive names for test files, classes, methods, and functions.
- Separate unit, integration, and end-to-end tests appropriately.
- Keep each test focused on one behavior or a clearly related set of assertions.
- Separate test setup, execution, and verification where appropriate.
- Reuse test helpers, fixtures, and utilities when they improve clarity and maintainability.
- Avoid unnecessary test duplication and overly complex test setup.
- Follow the conventions of the selected testing framework.

## 6. Test Quality and Coverage

- Aim for comprehensive and meaningful test coverage, prioritizing critical and complex parts of the codebase.
- Include positive, negative, boundary, and edge cases.
- Test invalid inputs, missing data, unexpected states, and failure conditions.
- Verify error handling and recovery behavior.
- Avoid tests that merely execute code without verifying meaningful outcomes.
- Avoid excessive mocking that hides integration problems.
- Use mocks and stubs only when they provide isolation or control over external dependencies.
- Keep tests deterministic and independent of execution order.
- Avoid arbitrary delays, uncontrolled network calls, and dependencies on external services.
- Do not pursue code coverage percentages at the expense of meaningful assertions.
- Ensure test names and assertions clearly communicate the expected behavior.

## 7. Test Data and Environment

- Use controlled, predictable, and reproducible test data.
- Keep test environments isolated from production environments.
- Never use real production credentials, secrets, or sensitive personal data.
- Clean up temporary resources and test data after execution.
- Avoid tests that depend on local machine configuration or execution order.
- Use environment-specific configuration for test environments.
- Make external dependencies explicit and controllable.
- Maintain test fixtures, datasets, mocks, and stubs as the codebase evolves.
- Regularly review and clean up test artifacts to prevent interference with future test runs.

## 8. Browser and UI Testing

For browser-based applications:

- Verify actual rendered behavior in a browser.
- Test initial page loading, navigation, and application initialization.
- Verify user interactions, forms, validation, and error states.
- Test keyboard navigation, focus behavior, and accessibility.
- Verify responsive layouts at narrow and wide viewport sizes.
- Check browser console errors and runtime exceptions.
- Verify loading, empty, success, and failure states.
- Test relevant touch, pointer, and keyboard interactions.
- Check for visual regressions after UI changes.
- Ensure essential content remains accessible independently of decorative elements.
- Verify rendering at different device-pixel ratios where relevant.

## 9. Test Execution and Automation

- Inspect the existing repository before selecting or introducing testing tools.
- Use the established test framework, runners, and tools configured for the project.
- Run relevant tests frequently during development to identify issues early.
- Execute affected tests after each meaningful implementation or refactoring change.
- Run broader regression tests before completing significant changes.
- Integrate automated tests into the existing Continuous Integration (CI) pipeline where available.
- Ensure CI provides consistent and reproducible test validation.
- Do not introduce additional testing dependencies without a clear technical justification.
- Do not invent test commands or assume scripts exist.
- If no test infrastructure exists, identify the gap and propose an appropriate setup before introducing one.
- Document new testing frameworks, configuration, dependencies, and execution commands.

## 10. Regression and Change Verification

After every relevant implementation change:

- Run newly created or modified tests.
- Run related regression tests.
- Verify that existing functionality remains intact.
- Check for unintended side effects in dependent components.
- Add regression tests for defects before or alongside implementing their fixes whenever practical.
- Investigate test failures instead of automatically updating expected results.
- Never disable existing tests without a documented technical justification.

## 11. Test Maintenance and Continuous Improvement

- Keep tests up-to-date with changes in the codebase.
- Remove or refactor obsolete, redundant, and unreliable tests.
- Review and improve test quality regularly.
- Investigate and resolve test failures promptly.
- Document known testing limitations and uncovered edge cases.
- Maintain test dependencies, mocks, fixtures, and configurations as the codebase evolves.
- Regularly review test scripts, configurations, and tooling to ensure compatibility with project changes.
- Keep test reporting and logging clear, actionable, and useful for diagnosing failures.
- Ensure test artifacts and temporary resources do not interfere with subsequent test runs.

## 12. Definition of Done

A task involving application behavior is not complete until:

- Relevant requirements have been translated into testable acceptance criteria.
- Appropriate tests have been created or updated.
- New functionality has been verified.
- Relevant regression tests have been executed.
- All relevant tests pass, or outstanding failures are explicitly reported.
- No known critical regressions remain.
- Test coverage is appropriate for the risk and complexity of the change.
- Documentation has been updated where necessary.

## 13. Test Reporting

When completing a task, provide a concise testing summary containing:

- **Tests added:** New or updated tests.
- **Testing approach:** TDD, BDD, or both.
- **Tests executed:** Actual commands and test suites executed.
- **Results:** Passed, failed, or skipped tests.
- **Manual verification:** Browser-based or exploratory checks performed.
- **CI status:** Relevant pipeline results, if available.
- **Outstanding issues:** Untested scenarios, limitations, or known failures.

Clearly distinguish automated testing from manual verification. Never report unexecuted tests as successful.