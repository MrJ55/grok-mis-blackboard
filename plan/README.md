# Plan — grok-mis-blackboard

**Last updated:** 2026-09-14 (seeded from design thread)

| Phase | File | Status | One-line |
|-------|------|--------|----------|
| P00 | P00-cold-start.md | planned | Bootstrap blackboard layout + bridge stub |
| P1 | P1-blackboard-schema.md | planned | Tasks/claims/results/receipts/queues schema |
| P2 | P2-bridge-watcher.md | planned | Per-sandbox detector + queue manager + ngrok client |
| P3 | P3-injection-path.md | planned | Align with MiS→bridge→ngrok→comet-mcp→CDP |
| P4 | P4-role-contracts.md | planned | Orchestrator / Generator / Analyst / Critic / Mutator |
| P5 | P5-async-workflow.md | planned | End-to-end task dispense → claim → result → receipt |
| P6 | P6-closed-loop-D.md | planned | Reflection → candidate → inject → promote cycle |
| P7 | P7-soft-autonomy-F.md | planned | Mind proposals via stack + constitutional host gate |
| P8 | P8-capacity-tiers.md | planned | Hot/warm/cold retention + compaction duties |
| P9 | P9-measurement.md | planned | Injection receipts, discharge rate, origin of permanent changes |

## Current focus

Seed complete. Begin P00 + P1 (layout and schema) so the blackboard can exist on disk and the bridge has a contract to implement.

## Design sources

This plan synthesizes the 2026-09-14 design thread covering:
- Ambient context / heartbeat injection
- Pure mind + bridge I/O boundary
- Shared artifacts as blackboard
- Async multi-role coordination without chat polling
- Gap analysis (comet-mcp cannot see artifacts; bridge must live in every sandbox)
- Closed-loop growth (D) and soft autonomy (F)
- Tiered capacity for exponential mind growth
