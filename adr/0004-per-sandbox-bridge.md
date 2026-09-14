# ADR 0004: Bridge present in every sandbox

- **Status:** Accepted
- **Date:** 2026-09-14

## Context

When a role posts a result/task, that tab may be the only live chat. Detection cannot depend on Orchestrator being online.

## Decision

1. **Bridge is part of standard bootstrap** for every participating session.
2. **Any sandbox** may detect blackboard changes and enqueue injection requests for other targets.
3. **comet-mcp** remains the only CDP injector; sandboxes push over ngrok.
4. **Per-target queues** under artifacts serialize wake-ups and avoid races when multiple stages target the same role.

## Consequences

- Fan-in of detectors is OK if enqueue is append-only and inject is idempotent by request id.
- Operational complexity: all role tabs need network to ngrok and bridge code in `/tmp/mis`.

## References

- Thread gap list items 4–5 [2026-09-14]
