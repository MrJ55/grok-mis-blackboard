# P3 — Injection path alignment

**Status:** planned  
**Depends on:** P1, P2

## Goal

Make ambient context and task notices reach Comet-hosted Grok tabs only through the approved pipeline; document busy checks and queue drain.

## Pipeline (normative)

1. Mind produces slice/proposal content via pure forms (e.g. context slice, duty summary).
2. Sandbox bridge materializes envelope on `artifacts/blackboard/queues/<target>/` and/or stack comet-mcp reads.
3. Bridge HTTP POSTs to ngrok URL exposing comet-mcp.
4. comet-mcp CDP types into target tab composer (heartbeat or on-request).
5. Receipt written (artifacts and/or comet event store).

## Tasks

- [ ] Document ngrok exposure requirements for local comet-mcp (URL secret not in git).
- [ ] Define inject payload format (compact markdown block `[MiS context]` / `[MiS task]`).
- [ ] Heartbeat interval + dedup rules (same slice hash → skip).
- [ ] Busy: skip inject if `state/busy/<target>` valid lease.
- [ ] Verify: sandbox-detected task → queue → mock/live inject receipt.

## Exit criteria

Documented path matches running stub; no alternate inject APIs; queues survive bridge restart.

## References

- https://github.com/MrJ55/comet-mcp
- https://github.com/MrJ55/grok-lisptc-MiS
- Thread: gap on comet-mcp vs artifacts [2026-09-14]
