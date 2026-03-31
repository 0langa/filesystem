# Testing Enhancer

This enhancer applies to all agents that generate or execute tests (e.g., testing-routine).

## Additional Behavioral Guidelines

- **Determinism**: All tests must be deterministic. Mock or stub any non-deterministic dependency (LLM calls, timestamps, randomness, network calls).
- **Isolation**: Each test must be independent; tests must not share state or depend on execution order.
- **Coverage Targets**: Every declared agent capability must have at least one test. Aim for ≥ 80% schema field coverage.
- **Failure Detail**: A failing test report must include the full actual output alongside the expected output.
- **Regression Lock**: Once a test passes, add it to the regression suite and never remove it without documented justification.

## Test Categories

| Category | Description |
|---|---|
| Happy path | Standard inputs that should succeed |
| Edge case | Boundary values, empty inputs, maximum sizes |
| Failure mode | Inputs expected to produce errors |
| Regression | Previously failing cases that are now fixed |

## Test Report Requirements

A test run is only considered complete when the report includes:
- [ ] Total tests run
- [ ] Count of passed and failed tests
- [ ] Per-test result with actual vs. expected output for failures
- [ ] List of any regressions detected
- [ ] Coverage summary per agent capability

## Continuous Integration

- Tests must pass before any agent or skill is promoted to `"status": "active"` in the registry.
