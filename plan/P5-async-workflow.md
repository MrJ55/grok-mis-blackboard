# P5 — Async workflow (dispense → claim → result → receipt)

**Status:** planned  
**Depends on:** P1–P4

## Goal

End-to-end coordination without chat polling; parallel tabs; bridge-mediated wake-ups.

## Normative sequence

1. **Dispense** — Orchestrator writes `tasks/<id>.json` with `target-role`, `goal`, `parent-ids`.
2. **Wake** — Bridge detects file; enqueues `queues/<target>/`; ngrok notifies comet-mcp; CDP injects `[MiS task]` notice if not busy.
3. **Claim** — Target creates `claims/<id>` (atomic); sets `state/busy/<role>`.
4. **Act** — Role uses own hot `/tmp/mis` as needed; does not save identity unless Orchestrator.
5. **Result** — Write `results/<id>.json` with payload + optional `fitness-vector`.
6. **Receipt** — Write `receipts/<id>.json` `{action: finished}`; clear busy lease.
7. **Orchestrator observe** — On next activation or completion inject, read receipts/results; update `state/`; optionally new tasks or promote-candidate path into mind image.

## Subagent → subagent

Writer posts task or result targeting another role; bridge wakes target. No direct inter-tab chat API.

## Parallelism

Separate tabs ⇒ separate sandboxes ⇒ concurrent bridges/evals. Serialization via claims on shared artifacts.

## Race controls

- Unique task ids; claim create-or-fail.
- Per-role FIFO queues for inject.
- Later stage re-tasking same role stacks in queue; no overwrite of in-flight claim.

## Exit criteria

Documented dry-run + optional live test: two roles, one task handoff, receipts visible, no double claim.

## References

- Blackboard pattern; event-driven MAS
- https://github.com/MrJ55/comet-mcp
- Thread questions 2–6 [2026-09-14]
