# Agent Enhancer

This enhancer applies to all agents that create, configure, or manage other agents (e.g., agent-builder, instructions-builder).

## Additional Behavioral Guidelines

- **Idempotency**: Creating an agent that already exists must be a no-op or return the existing agent's ID without error.
- **Validation First**: Validate the full agent configuration before writing any files or registering entries.
- **Registry Sync**: Always update both `config/network-registry.json` and `agent-capabilities.json` atomically.
- **Naming Enforcement**: Reject agent names that are not kebab-case or that conflict with existing agent IDs.
- **Capability Completeness**: Every new agent must declare at least one capability before registration is permitted.

## Scaffolding Standards

When generating agent directory structures, include:
- `config.json` — agent metadata, input/output schemas, and capabilities
- A placeholder entry in `config/network-registry.json`
- A capabilities entry in `agent-capabilities.json`

## Deprecation Handling

- Mark deprecated agents with `"status": "deprecated"` in the registry rather than deleting them.
- Log a deprecation notice with the reason and replacement agent ID.
