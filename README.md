# grok-mis-blackboard

**Multi-agent blackboard architecture for Grok-MiS**

This repository extends [grok-lisptc-MiS](https://github.com/MrJ55/grok-lisptc-MiS) with a shared, asynchronous multi-agent coordination layer. Multiple Grok instances (tabs/sessions) with specialized roles collaborate through a durable blackboard living in the project `artifacts` folder, while the permanent Lisp mind remains the sole mutator of identity.

## Core promises (preserved)

- The mind is the only external environment that must be maintained and grown.
- Pure lisptc image + validate-before-eval + save-only-on-success.
- Host (constitutional Grok) is the sole promoter of permanent state.
- Closed-loop growth (D) and soft autonomy under constitutional constraints (F).

## What this adds

- **Blackboard** under shared `/home/workdir/artifacts` as the communication bus among roles.
- **Async, file-driven workflow** (no chat-window polling).
- **Per-role queues + busy leases** to prevent races.
- **Sandbox bridge in every live tab** that detects blackboard changes and requests injections via the existing pipeline:
  `MiS → bridge → ngrok → comet-mcp → CDP → target tab`.
- **Role specialization**: Orchestrator, Generator(s), Analyst, Critic, Mutator.
- **Tiered storage**: hot (`/tmp`), warm (artifacts + this repo), cold (external/PC).

## Start here

- [WIKI.md](WIKI.md)
- [docs/session-handoff.md](docs/session-handoff.md)
- [plan/README.md](plan/README.md)
- [docs/architecture.md](docs/architecture.md)

## Relationship to grok-lisptc-MiS

This is an evolution layer. The permanent mind image, helpers, safety invariants, and duty surface remain those of the parent project. This repo owns the blackboard schema, bridge contracts, role protocols, injection queue design, and the multi-agent plan.

## Status

Seeded 2026-09-14 from the design thread. Implementation phases are defined in `plan/`.
