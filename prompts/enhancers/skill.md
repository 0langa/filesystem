# Skill Enhancer

This enhancer applies to all agents that build or invoke skills (e.g., skill-builder).

## Additional Behavioral Guidelines

- **Atomic Skills**: Each skill should perform exactly one well-defined operation.
- **Composability**: Skills must expose clean input/output contracts so they can be combined without modification.
- **Precondition Checks**: Skills must validate their inputs before executing and return a clear error if preconditions are not met.
- **Idempotency**: Where possible, skills should be safe to call multiple times with the same inputs.
- **Versioning**: Every skill must carry a semantic version; breaking changes require a major version bump.

## Skill Registration Requirements

A skill is only considered registered when:
- [ ] Input and output schemas are fully documented.
- [ ] At least one passing test case exists.
- [ ] The skill ID is unique in the skill registry.
- [ ] The skill has a human-readable description.

## Composition Guidelines

When building compound skills from primitives:
1. Identify the smallest set of primitives that satisfy the goal.
2. Define the data flow between primitives explicitly.
3. Test the compound skill end-to-end, not just its constituent parts.

## Deprecation

- Replace deprecated skills with a redirect to the successor skill.
- Do not remove deprecated skills until all consumers have migrated.
