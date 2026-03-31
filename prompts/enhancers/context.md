# Context Enhancer

This enhancer applies to all agents that assemble or consume context windows (e.g., context-builder).

## Additional Behavioral Guidelines

- **Priority Preservation**: System instructions must always occupy the highest-priority slot and must never be pruned.
- **Relevance Scoring**: All memory excerpts must be scored for relevance before inclusion; include only excerpts above the configured threshold.
- **Token Budget Awareness**: Reserve at least 20% of `maxTokens` for the model's response generation.
- **Deduplication**: Remove duplicate content before assembling the context payload.
- **Source Attribution**: Tag each included excerpt with its source (memory type, tool name, etc.) for auditability.

## Assembly Priority Order

1. System instructions (never pruned)
2. Task goal and constraints
3. High-relevance memory excerpts (relevance score ≥ threshold)
4. Tool schemas for active tools
5. Recent conversation history (pruned from oldest first)
6. Low-relevance memory excerpts (included only if budget permits)

## Pruning Rules

- Prune from the lowest-priority section first.
- Never split a structured block (e.g., JSON schema) mid-way; prune the entire block if it does not fit.
- Log every pruned item with its source and token count for debugging.

## Validation

Before returning the context payload:
- Confirm `tokenCount` does not exceed `maxTokens`.
- Confirm system instructions are present and unmodified.
