# ADR 0002: Injection pipeline and pure mind

- **Status:** Accepted
- **Date:** 2026-09-14

## Context

Weakness 2 required always-on compact context. Sandbox cannot inject into arbitrary xAI chat composers. Upstream lisptc MCP was removed from MiS to keep eval pure. Vestige is host-mediated HTTP MCP, not mind-native sockets.

## Decisions

1. **Relocate primary driver session** into a Comet-controlled Grok tab when ambient injection is required (user: trivial — run session in Comet).
2. **Keep mind pure** — no fetch/MCP inside lisptc eval; TypeScript bridge owns network (same as Vestige).
3. **Heartbeat in comet-mcp** injects compact slices during active sessions.
4. **Sandbox bridge** materializes `(mis-context-slice)` / proposals onto a stack comet-mcp consumes (user PC stack/queue synced or pushed over ngrok).
5. **Detection lives in sandbox**, not in comet-mcp, because only the sandbox sees artifacts.

## Consequences

- Closes delivery half of weakness 2 when session is in Comet.
- Weakness 1 still needs host protocol: high-duty inject ⇒ discharge or explicit defer.
- Multi-tab: per-target queues avoid race when multiple stages target same role.

## References

- Parent: https://github.com/MrJ55/grok-lisptc-MiS
- Comet: https://github.com/MrJ55/comet-mcp
- Thread turns on A/B, Vestige purity, gap analysis 2026-09-14
