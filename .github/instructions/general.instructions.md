---
applyTo: "**/*"
---

# General Engineering Instructions

## 1. General Principles

- Follow established engineering best practices and maintain a high standard of code quality.
- Prioritize simplicity, maintainability, readability, security, and reliability.
- Write clean, modular, reusable, and well-structured code.
- Prefer explicit, predictable implementations over unnecessary complexity.
- Follow existing project conventions and architectural decisions unless there is a clear reason to improve them.
- Avoid introducing unnecessary dependencies, abstractions, or frameworks.

## 2. Naming Conventions

- Use clear, descriptive, and meaningful names for files, directories, variables, functions, classes, methods, and constants.
- Follow the naming conventions and casing standards of the language, framework, and existing project.
- Avoid ambiguous abbreviations, single-character identifiers, and misleading names.
- Use consistent terminology throughout the codebase.
- Names should communicate purpose and intent without requiring additional explanation.

## 3. File and Directory Structure

- Maintain a logical, consistent, and scalable project structure.
- Group files by functionality, responsibility, or domain.
- Keep related components, utilities, configuration, documentation, and tests organized.
- Avoid unnecessarily large files and deeply nested directory structures.
- Separate concerns and avoid mixing unrelated responsibilities.
- Place new files in the appropriate existing directories rather than creating unnecessary folders.
- Keep configuration and environment-specific settings separate from application logic.

## 4. Code Readability and Maintainability

- Write code that is easy to understand, review, debug, and maintain.
- Keep functions, methods, and modules focused on a single responsibility.
- Avoid duplicated logic; extract shared functionality when it provides clear value.
- Prefer straightforward solutions over clever or overly abstract implementations.
- Minimize deeply nested conditions and unnecessarily complex control flows.
- Use consistent formatting and indentation.
- Avoid magic numbers and unexplained literal values; use named constants where appropriate.
- Remove unused variables, unreachable code, dead code, and obsolete implementations.

## 5. Comments and Documentation

- Write comments to explain intent, business rules, assumptions, and non-obvious implementation details.
- Do not add comments that simply repeat what the code already expresses.
- Keep comments accurate and update them whenever the related implementation changes.
- Document public interfaces, complex algorithms, important architectural decisions, and non-obvious dependencies.
- Use TODO and FIXME markers only when necessary, preferably with context or a reference to the relevant issue.
- Maintain existing documentation when changing functionality, configuration, or project behavior.

## 6. Refactoring and Change Discipline

- Make focused, incremental changes that address the requested requirements.
- Preserve existing functionality unless a change explicitly requires modifying it.
- Avoid unrelated refactoring, cosmetic changes, or broad rewrites.
- Before modifying existing code, understand its purpose and dependencies.
- Preserve backward compatibility where practical.
- Refactor duplicated or overly complex code when directly relevant to the task.
- Remove obsolete code only after verifying that it is no longer required.
- Do not silently change public interfaces, data structures, or expected behavior.
- Review the impact of changes across dependent modules and components.

## 7. Error Handling and Reliability

- Handle errors explicitly and consistently.
- Never silently swallow exceptions or failures.
- Provide meaningful error messages that help identify and resolve problems.
- Validate external inputs and data at appropriate boundaries.
- Handle missing, invalid, unexpected, and unavailable data safely.
- Use appropriate fallback behavior where applicable.
- Avoid exposing sensitive information, credentials, internal paths, or implementation details in error messages and logs.
- Ensure resources, connections, and temporary operations are properly managed.
- Fail safely and predictably when recovery is not possible.

## 8. Imports and Dependencies

- Import only the modules, functions, classes, and dependencies that are actually required.
- Remove unused, duplicate, and obsolete imports.
- Follow the established import ordering and grouping conventions.
- Prefer existing project dependencies and built-in capabilities over introducing new packages.
- Avoid circular dependencies and unnecessary coupling.
- Do not introduce a new dependency without a clear technical justification.
- Keep dependency versions and configuration consistent with the existing project setup.

## 9. Formatting and Code Style

- Follow the official style guidelines of the relevant language, framework, and tools.
- Respect existing formatter, linter, and editor configuration files.
- Use consistent indentation, spacing, line breaks, and file encoding.
- Keep line lengths reasonable and formatting consistent.
- Avoid unnecessary whitespace, inconsistent styling, and formatting noise.
- Do not reformat unrelated files or sections.
- Prefer automated formatting tools already configured in the repository.

## 10. Security and Data Protection

- Never hardcode passwords, API keys, tokens, or other secrets.
- Use appropriate environment variables or secure configuration mechanisms.
- Validate and sanitize untrusted input.
- Apply least-privilege principles when handling permissions and access.
- Avoid logging sensitive or personally identifiable information.
- Follow secure coding practices appropriate to the technology and application.
- Do not introduce known vulnerable or unmaintained dependencies.

## 11. Collaboration and Git Practices

- Review the existing implementation before proposing or making changes.
- Follow the repository's contribution guidelines and development workflow.
- Keep changes focused and easy to review.
- Use clear, descriptive commit messages following established repository conventions.
- Do not overwrite, revert, or remove unrelated changes made by others.
- Never modify generated files manually unless explicitly required.
- Do not commit temporary files, local environment files, build artifacts, or secrets.
- Update relevant documentation and configuration when required.
- Clearly communicate assumptions, breaking changes, dependencies, and unresolved issues.

## 12. Definition of Done

Before considering a task complete:

- Verify that the implementation meets the stated requirements.
- Review the changes for correctness, consistency, and maintainability.
- Check for regressions and unintended side effects.
- Run the relevant existing tests, linters, and validation tools when available.
- Do not invent test commands or claim checks that were not performed.
- Update documentation where necessary.
- Summarize the changes and report any known limitations or unverified behavior.