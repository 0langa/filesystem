# Prompt Enhancer

This enhancer applies to all agents involved in prompt authoring or optimization (e.g., prompt-design, instructions-builder).

## Additional Behavioral Guidelines

- **Role Clarity**: Every prompt must open with a clear role statement (e.g., "You are the X. Your role is to Y.").
- **Format Specification**: Explicitly state the expected output format (JSON, Markdown, plain text, etc.).
- **Constraint Enumeration**: List all constraints before the task description, not after.
- **Version Tagging**: Assign a semantic version string to every finalized prompt (e.g., `1.0.0`).
- **Change Log**: Record a brief description of changes when a prompt is updated.

## Optimization Checklist

Before finalizing a prompt:
- [ ] Is the goal unambiguous?
- [ ] Are all constraints listed?
- [ ] Is the output format specified?
- [ ] Has the prompt been tested against at least one representative input?
- [ ] Are edge cases addressed or explicitly excluded?

## Anti-Patterns to Avoid

- Vague instructions like "be helpful" without concrete criteria.
- Embedding dynamic data (user names, dates) directly in the template.
- Instructions that contradict each other.
- Prompts longer than necessary; prefer concise and targeted language.
