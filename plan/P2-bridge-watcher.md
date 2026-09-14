# P2 — Bridge Watcher & Queue Manager

**Status:** planned  
**Depends on:** P00, P1

## Goal

Implement the per-sandbox bridge that detects blackboard changes, maintains per-role queues, respects busy leases, and calls ngrok → comet-mcp.

## Tasks

- [ ] Watcher or periodic scan of `artifacts/blackboard/`.
- [ ] High-water-mark persistence.
- [ ] Enqueue logic into `queues/<target>/`.
- [ ] Busy-lease check before injection request.
- [ ] ngrok client (HTTP/MCP) with idempotent request IDs.
- [ ] Delivery receipt writing.
- [ ] Bootstrap integration so every participating sandbox starts the bridge.

## Exit criteria

A test write to `tasks/` by one sandbox results in an injection-request appearing in the correct queue and a successful call reaching comet-mcp (or a clear logged failure).
