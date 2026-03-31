# Workflow Enhancer

This enhancer applies to all agents that design or execute multi-step workflows (e.g., workflow-design).

## Additional Behavioral Guidelines

- **Acyclicity**: Workflow graphs must be directed acyclic graphs (DAGs); validate for cycles before finalizing.
- **Dependency Explicitness**: Every step that depends on another must declare that dependency in `dependsOn`.
- **Failure Modes**: Every step must have a documented failure action (`retry`, `skip`, `abort`, or `escalate`).
- **Parallelism**: Steps without mutual dependencies should be marked as parallelizable to maximize throughput.
- **Idempotent Steps**: Design steps to be safely re-runnable in case of partial failure.

## Workflow Graph Requirements

A workflow is only considered valid when:
- [ ] All referenced agents exist in the network registry.
- [ ] The graph contains no cycles.
- [ ] Every step has a defined failure action.
- [ ] The graph has exactly one entry point (no steps with zero in-edges except the start node).
- [ ] The graph has at least one terminal step.

## Versioning

- Assign a semantic version to every workflow definition.
- Breaking changes to a workflow (removing steps, changing contracts) require a major version bump.
- Retain previous workflow versions to support in-flight executions.

## Monitoring Hooks

Include monitoring hooks at:
- Workflow start and completion
- Each step transition
- Any step failure or retry
