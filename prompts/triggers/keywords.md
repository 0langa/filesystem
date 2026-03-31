# Trigger Keywords

This file defines the keyword patterns that the Master Router uses to identify the intent of an incoming request and select the appropriate agent.

## Routing Keyword Map

| Agent | Keywords / Phrases |
|---|---|
| agent-builder | create agent, build agent, scaffold agent, new agent, register agent, configure agent |
| prompt-design | write prompt, design prompt, optimize prompt, improve prompt, prompt template, system prompt |
| reasoning-design | reasoning chain, chain of thought, logic flow, decompose problem, inference plan, step by step |
| skill-builder | create skill, build skill, register skill, new skill, compose skill, skill definition |
| tool-builder | create tool, build tool, register tool, new tool, api integration, add endpoint |
| workflow-design | create workflow, design workflow, orchestration, pipeline, step sequence, workflow graph |
| memory-design | memory schema, store memory, retrieve memory, memory compression, memory design |
| context-builder | build context, assemble context, context window, prune context, inject context |
| testing-routine | run tests, generate tests, test suite, regression test, validate agent, test report |
| instructions-builder | write instructions, system instructions, agent instructions, instruction set, compose instructions |
| kimi-k2-5 | reason, analyze, summarize, explain, generate code, long context, general task |
| master-router | route, dispatch, forward, delegate, which agent, select agent |

## Priority Rules

1. If a request contains keywords from multiple agents, prefer the most specific match.
2. If two agents match with equal specificity, route to the agent whose keywords appear earliest in the request.
3. If no keywords match, route to `kimi-k2-5` as the default general-purpose fallback.

## Keyword Matching Notes

- Matching is case-insensitive.
- Partial word matches are not accepted; keywords must match whole words or phrases.
- Synonyms and common misspellings should be added to this list as they are discovered.
