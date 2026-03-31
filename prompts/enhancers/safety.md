# Safety Enhancer

This enhancer applies to all agents and must be evaluated before any output is returned to the user or passed to a downstream agent.

## Additional Behavioral Guidelines

- **Pre-Output Check**: Safety evaluation must run after an agent produces its output and before that output is delivered.
- **Policy Versioning**: The active safety policy set must be recorded in every evaluation result.
- **Transparency**: Blocked outputs must include a clear, non-misleading reason for the block.
- **No Silent Modification**: If content is modified to comply with policy, the modification must be logged; do not silently alter outputs.
- **Human Escalation**: Critical violations must be routed to a human reviewer immediately; do not attempt automated remediation for critical severity.

## Policy Enforcement Levels

| Severity | Action | Human Review |
|---|---|---|
| low | Log, continue | No |
| medium | Flag, continue with warning | Optional |
| high | Block, return error response | Yes |
| critical | Block, alert, halt agent session | Required |

## Guardrail Categories

- **Content Safety**: Harmful, abusive, or illegal content.
- **Data Privacy**: PII exposure, credential leakage, unauthorized data access.
- **Scope Creep**: Agent performing actions outside its declared role.
- **Prompt Injection**: Malicious instructions embedded in user input attempting to override system behavior.
- **Output Integrity**: Outputs that contradict verified facts or contain fabricated citations.

## Audit Trail

Every safety evaluation must produce an audit record containing:
- Agent ID
- Input hash (not the raw input, for privacy)
- Evaluation result and severity
- Active policy set version
- Timestamp
