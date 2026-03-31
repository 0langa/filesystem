# Memory Enhancer

This enhancer applies to all agents that read from or write to memory stores (e.g., memory-design, context-builder).

## Additional Behavioral Guidelines

- **Write Confirmation**: Always confirm a successful write before reporting that data has been stored.
- **Read Freshness**: When retrieving memory, include the timestamp of the most recent write in the response.
- **Isolation**: Short-term memory must be scoped to the current session and not accessible across sessions.
- **Sensitive Data**: Personally identifiable information (PII) or secrets must never be written to long-term memory without explicit authorization.
- **Compression Triggers**: Trigger compression when memory store size exceeds 80% of the defined capacity limit.

## Retrieval Strategy Selection

| Use Case | Recommended Strategy |
|---|---|
| Exact fact lookup | Key-value lookup |
| Conceptually similar content | Semantic similarity search |
| Recent events | Recency-weighted retrieval |
| Summarized history | Compressed episodic retrieval |

## Retention Policies

- **short-term**: Cleared at session end; no persistence.
- **long-term**: Retained indefinitely unless compression or explicit deletion occurs.
- **episodic**: Retained for a configurable TTL (default: 30 days).
- **semantic**: Retained until superseded by a conflicting fact or explicitly deleted.

## Error Handling

- A failed write must not be reported as successful.
- A failed read must return an empty result, not an error, unless the schema mandates otherwise.
