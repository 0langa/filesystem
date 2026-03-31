# Router Output Schema

This document defines the standard output schema that the Master Router must use for every routing decision.

## Schema

```json
{
  "requestId": "string",
  "status": "string",
  "route": {
    "agentId": "string",
    "agentPath": "string",
    "host": "string",
    "port": 0
  },
  "subRoutes": [
    {
      "agentId": "string",
      "agentPath": "string",
      "subtask": "string"
    }
  ],
  "confidence": 0.0,
  "matchedKeywords": ["string"],
  "reason": "string",
  "timestamp": "string"
}
```

## Field Descriptions

| Field | Type | Required | Description |
|---|---|---|---|
| requestId | string | Yes | Unique identifier for the incoming request |
| status | string | Yes | One of: `routed`, `multi-routed`, `unrouted`, `error` |
| route | object | When status = `routed` | Primary agent destination |
| route.agentId | string | Yes (if route present) | ID of the target agent |
| route.agentPath | string | Yes (if route present) | Filesystem path to the agent |
| route.host | string | No | Target host, if load-balanced |
| route.port | number | No | Target port, if load-balanced |
| subRoutes | array | When status = `multi-routed` | List of sub-task routes for decomposed requests |
| subRoutes[].agentId | string | Yes (per sub-route) | ID of the sub-task agent |
| subRoutes[].agentPath | string | Yes (per sub-route) | Filesystem path to the sub-task agent |
| subRoutes[].subtask | string | Yes (per sub-route) | Description of the sub-task assigned to this agent |
| confidence | number | Yes | Routing confidence score between 0.0 and 1.0 |
| matchedKeywords | array | Yes | Keywords that triggered this routing decision |
| reason | string | Yes | Human-readable explanation of the routing decision |
| timestamp | string | Yes | ISO 8601 timestamp of the routing decision |

## Status Values

| Status | Meaning |
|---|---|
| `routed` | Request matched a single agent and has been dispatched |
| `multi-routed` | Request was decomposed into multiple sub-tasks, each routed to a different agent |
| `unrouted` | No matching agent found; see `reason` for details |
| `error` | An internal routing error occurred; see `reason` for details |

## Example

```json
{
  "requestId": "req-00142",
  "status": "routed",
  "route": {
    "agentId": "prompt-design",
    "agentPath": "agents/prompt-design",
    "host": "host1.local",
    "port": 8080
  },
  "subRoutes": [],
  "confidence": 0.95,
  "matchedKeywords": ["optimize prompt", "prompt template"],
  "reason": "Request matched prompt-design via 'optimize prompt' and 'prompt template' keywords.",
  "timestamp": "2026-03-31T02:00:00.000Z"
}
```
