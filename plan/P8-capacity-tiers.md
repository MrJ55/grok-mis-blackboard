# P8 — Capacity / tiered retention

**Status:** planned  
**Depends on:** P1, parent capacity discussion 2026-09-14

## Goal

Prevent unbounded growth from closed-loop D/F from exhausting sandbox RAM (~1.2GiB, no swap) or drowning host context. Canonical mind stays on warm tier (artifacts + GitHub); `/tmp/mis` remains disposable hot cache.

## Tiers

| Tier | Location | Content |
|------|----------|--------|
| Hot | `/tmp/mis` | Working image copy, short eval process |
| Warm | `artifacts` + GitHub | mind-image, modules, schema, current autobiography, compact episodic window, blackboard |
| Cold | User PC / external | Full history, old chapters, raw OSS logs, vector dumps |

## Tasks

- [ ] Soft budgets: hot text size, episodic buffer length thresholds → compaction duty.
- [ ] `(mind-capacity)` or extend `mis-state-summary` with bytes/module/buffer metrics.
- [ ] Compaction forms: summarize episodes, archive chapters to cold path instructions.
- [ ] Document rsync/git export to PC as cold tier (no remote RAM mount).
- [ ] Blackboard channel retention: move old envelopes to `archive/`.

## Exit criteria

Capacity metrics visible; compaction path documented; hot rebuild from warm verified.

## References

- Thread capacity analysis [2026-09-14]
- Parent push-mind-image.sh
- https://github.com/MrJ55/grok-lisptc-MiS
