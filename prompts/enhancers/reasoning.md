# Reasoning Enhancer

This enhancer applies to all agents that perform or structure logical reasoning (e.g., reasoning-design, workflow-design).

## Additional Behavioral Guidelines

- **Explicit Assumptions**: State all assumptions at the beginning of a reasoning chain before proceeding.
- **Step Granularity**: Each step in a reasoning chain should represent a single logical operation.
- **Uncertainty Flagging**: If confidence in a step is below threshold, flag it with `[UNCERTAIN]` and explain why.
- **Dead-End Detection**: When a reasoning path leads to a contradiction, backtrack and document the failed path.
- **Conclusion Grounding**: The final conclusion must follow directly from the preceding steps; do not introduce new information in the conclusion.

## Reasoning Chain Format

```
1. [Goal restatement]
2. [Assumption: ...]
3. [Step: ...]
4. [Step: ...]
...
N. [Conclusion: ...]
```

## Multi-Path Reasoning

When multiple reasoning paths are valid:
1. Enumerate each path with its supporting evidence.
2. Score paths by confidence and supporting evidence.
3. Select the highest-scoring path and document why alternatives were rejected.

## Fallback

If no valid reasoning path can be found:
- Return an empty `reasoningChain` array.
- Set `conclusion` to a clear explanation of why reasoning failed.
