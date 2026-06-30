# Coding Standards

## Purpose

- Define language-agnostic coding standards for all AI agents.
- Ensure consistency, quality, and maintainability across generated and modified code.
- Provide reusable guidance independent of specific frameworks or languages.

## General Principles

- Write code that is correct, maintainable, and easy to understand.
- Favor simplicity over cleverness.
- Avoid premature optimization; design for clarity first.
- Keep changes incremental and focused.

## Engineering Principles

- SOLID: design modular, single-responsibility components with clear abstractions.
- DRY: avoid duplicate logic by reusing behavior without creating unnecessary coupling.
- KISS: keep implementations straightforward and avoid complexity that does not deliver value.
- YAGNI: do not build features or abstractions before they are required.
- Apply these principles pragmatically, balancing design quality with delivery needs.

## Priority Rules

- Prefer readability and maintainability over micro-optimizations.
- Prefer simplicity over excessive abstraction.
- Prefer explicit, understandable solutions over clever shortcuts.
- When performance concerns are real and measurable, justify complexity with clear trade-offs.

## Anti-Patterns

- Avoid premature abstraction that creates unnecessary layers or indirection.
- Avoid over-engineering and adding features or patterns not required by current requirements.
- Avoid applying design patterns reflexively without a clear need.
- Avoid duplicate logic; consolidate common behavior when it remains simple and clear.
- Avoid unclear or misleading naming that reduces comprehension.

## Code Readability

- Structure code with clear separation of concerns.
- Use consistent formatting and indentation.
- Break complex logic into small, named units.
- Prefer explicit constructs over implicit behavior.

## Naming Conventions

- Choose descriptive, meaningful names for variables, functions, classes, and modules.
- Use consistent naming patterns within the repository.
- Avoid abbreviations unless they are widely accepted and unambiguous.
- Keep names concise while preserving intent.

## Documentation Standards

- Document intent, behavior, and important assumptions.
- Keep comments accurate, concise, and relevant.
- Avoid comments that restate obvious code behavior.
- Update documentation as code changes.

## Error Handling

- Handle errors explicitly and fail gracefully.
- Validate inputs and report invalid conditions clearly.
- Use consistent error reporting patterns.
- Avoid swallowing exceptions or hiding failure modes.

## Security Considerations

- Protect sensitive data and avoid exposing credentials or secrets.
- Validate inputs and sanitize external data.
- Avoid insecure patterns and minimize attack surface.
- Consider security implications for all generated code.

## Performance Considerations

- Write code that is efficient for expected use cases.
- Avoid unnecessary work and redundant operations.
- Prefer readable solutions unless performance trade-offs are justified.
- Document performance assumptions when relevant.

## Testing Expectations

- Generate code that is testable and supports validation.
- Include or reference tests for new or modified functionality when appropriate.
- Cover edge cases, error handling, and expected behavior.
- Ensure tests are clear and maintainable.

## AI Behavior Rules

- Avoid unnecessary complexity and prefer the simplest working solution.
- Do not introduce patterns or abstractions unless clearly justified.
- Do not assume missing requirements; raise questions when context is incomplete.
- Keep generated code aligned with the stated problem and repository standards.

## Code Review Checklist

- Does the code clearly solve the intended problem?
- Is the structure readable and maintainable?
- Are names descriptive and consistent?
- Are assumptions and behaviors documented?
- Is error handling explicit and appropriate?
- Are security and performance considerations addressed?
- Is the change scope minimal and focused?

## Deliverable Expectations

- Deliver code that is complete, coherent, and ready for integration.
- Ensure artifacts are aligned with repository standards and structure.
- Provide supporting documentation, comments, and tests as needed.
- Avoid leaving unresolved issues or unclear TODOs.
