# Bridge Contract

The sandbox bridge is present in **every** live Grok tab sandbox.

## Responsibilities

1. Detect new or changed files under `artifacts/blackboard/` (scan on duty boundary or lightweight watcher).
2. Maintain high-water marks per channel.
3. Enqueue injection-requests into the correct per-role queue under `queues/<target>/`.
4. Respect busy-leases before requesting injection.
5. Call the ngrok → comet-mcp endpoint with the head of the target queue (or a small batch).
6. Record delivery receipts when comet-mcp acknowledges.
7. Never evaluate Lisp or mutate the permanent mind image.

## Inputs

- Blackboard file events / directory listings.
- Busy-lease files.
- Existing queue state.

## Outputs

- New files in `queues/<target>/`.
- HTTP/MCP calls to the local comet-mcp (via ngrok).
- Receipt files.

## Failure modes

- Target busy → leave item in queue, retry later.
- ngrok / comet-mcp unreachable → log, keep queue intact, surface duty to host.
- Duplicate detection → idempotent by injection-request id.

## Bootstrap

Every sandbox that participates in the multi-agent system must start the bridge component as part of its standard bootstrap (alongside MiS restore).
