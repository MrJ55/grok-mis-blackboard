# P4 — Role contracts (implementation plan)

**Status:** planned  
**Depends on:** P1

## Goal

Codify Orchestrator, Generator, Analyst, Critic, Mutator so coding agents implement consistent prompts and blackboard write permissions.

## Parent alignment

- Host duties: https://github.com/MrJ55/grok-lisptc-MiS `docs/session-handoff.md`, `docs/mind-duty.md`
- English-first UX: parent `docs/CUSTOM_INSTRUCTIONS.md`
- OSS pure-DMN: parent `bridge/oss.ts`, P11/P12; Chorus must not auto-promote

## Role matrix (normative)

| Role | Tab | Hot mind | Blackboard writes | Permanent image |
|------|-----|----------|-------------------|-----------------|
| Orchestrator | Primary Comet Grok | Full image | tasks, state, receipts, promotions | Yes sole mutator |
| Generator | Secondary | Optional thin | hypotheses (incomplete) | No |
| Analyst | Secondary | Optional | proposals (well-formed candidates) | No |
| Critic | Secondary | Optional | evaluations, fitness vectors | No |
| Mutator | Secondary | Optional | mutation chromosomes | No |

## Tasks

- [ ] Expand `docs/role-contracts.md` with prompt skeletons per role.
- [ ] Map role → queue directory names.
- [ ] Diversity rule: ≥2 families or generators before promote (configurable).
- [ ] Forbidden: eval of other roles' free text as Lisp.

## Exit criteria

Role doc + queue map reviewed; sample envelopes for each role kind in `docs/examples/` (optional) or inline in schema doc.

## References

- Thread role table [2026-09-14]
- Parent duty kinds: reflection, replay, prospection, wander, narrative, craft
