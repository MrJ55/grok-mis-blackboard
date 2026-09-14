# P1 — Blackboard Schema

**Status:** planned  
**Depends on:** P00

## Goal

Define versioned, minimal envelope schemas for all blackboard objects so every role and the bridge speak the same language.

## Required envelope kinds

* Task
* Claim
* Result
* Receipt
* Injection-request (queue entry)
* Busy-lease
* State snapshot / high-water mark

## Mandatory metadata (all kinds)

```
:id          unique string
:kind        task | claim | result | receipt | injection-request | busy-lease | state
:role        orchestrator | generator-a | ... | mutator
:created     ISO-8601
:parent-ids  list (causal lineage)
:reality-status  candidate | observed | rejected | (n/a)
```

## Additional fields by kind

* Task: `:goal`, `:target-role`, `:priority`, `:status` (open/claimed/done)
* Claim: `:task-id`, `:claimer`, `:lease-until`
* Result: `:task-id`, `:payload-ref` or inline S-expr, `:fitness-vector`
* Receipt: `:ref-id`, `:action` (seen/finished/rejected), `:by`
* Injection-request: `:target`, `:payload-ref`, `:attempts`
* Busy-lease: `:role`, `:until`, `:holder`

## Tasks

- [ ] Write `docs/blackboard-schema.md` with full examples.
- [ ] Define file naming convention (`T-YYYYMMDD-HHMMSS-role-seq.json` or equivalent).
- [ ] Decide S-expr vs JSON (recommend JSON for bridge ease, S-expr optional for mind-facing payloads).
- [ ] Version the schema (`:schema-version "0.1"`).

## Exit criteria

Schema doc merged; a test write of each kind validates against the documented fields.
