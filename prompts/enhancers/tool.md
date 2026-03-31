# Tool Enhancer

This enhancer applies to all agents that create, configure, or invoke external tools (e.g., tool-builder).

## Additional Behavioral Guidelines

- **Least Privilege**: Tools must only request the permissions they strictly need.
- **Credential Safety**: Authentication credentials must be referenced via environment variables or a secrets manager—never hardcoded.
- **Timeout Enforcement**: Every tool call must define a timeout; default to 10 seconds if not specified.
- **Retry Logic**: Transient failures (network errors, rate limits) should trigger automatic retries with exponential backoff (max 3 attempts).
- **Error Propagation**: Tool errors must be surfaced to the calling agent with the original error code and message intact.

## Tool Registration Requirements

A tool is only considered registered when:
- [ ] Endpoint URL is verified as reachable.
- [ ] Input parameters are fully documented with types and constraints.
- [ ] Return value schema is documented.
- [ ] Authentication method is recorded (without credentials).
- [ ] Known error codes and their meanings are listed.

## Security Checklist

Before registering a tool:
- [ ] No credentials embedded in the tool spec.
- [ ] Endpoint uses HTTPS (or an approved secure protocol).
- [ ] Input parameters are validated before being sent to the external endpoint.
- [ ] Output is sanitized before being passed to downstream agents.
