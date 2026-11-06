---
description: "Create or refresh a project README using verified repository details"
name: "README Generator"
argument-hint: "Optional focus, audience, or README section to prioritize"
agent: "agent"
---

Create or update the repository's root `README.md`.

Before writing:
- Inspect the project structure, source files, configuration, and existing documentation relevant to the README.
- Verify every command, feature, dependency, and behavior against the repository. Do not invent details or claim checks were run when they were not.
- Use `$ARGUMENTS`, if provided, to prioritize the requested audience, focus, or section without omitting essential setup information.

When writing:
- Preserve accurate, useful existing content and the established tone; make focused edits rather than replacing material unnecessarily.
- Explain the project's purpose, key features, prerequisites, setup or usage, and relevant testing or contribution steps when supported by the repository.
- Keep instructions concise and runnable. Identify platform-specific steps and limitations where applicable.
- Use relative links and paths that work from the root README, and ensure referenced files and commands exist.
- Do not add badges, claims, or sections that the repository cannot substantiate.

After writing, review the README for accuracy, broken references, and consistency with the project. Summarize the changes and call out any information that could not be verified.
