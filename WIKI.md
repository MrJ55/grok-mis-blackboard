# Wiki — grok-mis-blackboard

Multi-agent blackboard layer on top of grok-lisptc-MiS.

## Start here

* [README.md](README.md)
* [docs/session-handoff.md](docs/session-handoff.md)
* [plan/README.md](plan/README.md)
* [docs/architecture.md](docs/architecture.md)
* [docs/blackboard-schema.md](docs/blackboard-schema.md)
* [docs/bridge-contract.md](docs/bridge-contract.md)
* [docs/role-contracts.md](docs/role-contracts.md)

## Architecture summary

- **Mind** (lisptc image): sole mutator of permanent identity. Pure, no network.
- **Blackboard** (`artifacts/blackboard/`): shared async bus for tasks, claims, results, receipts, per-role queues.
- **Bridge** (every sandbox): detects blackboard changes, manages queues, requests injections via ngrok → comet-mcp.
- **comet-mcp + Comet**: CDP injection into the correct Grok tab. No direct access to artifacts.
- **Roles**: Orchestrator (constitutional host), Generator(s), Analyst, Critic, Mutator — each can run in its own tab with its own hot `/tmp/mis`.

## Key invariants

1. Permanent image changes only through MiS validate → eval → save-on-success.
2. Blackboard holds candidates and coordination state only.
3. Injection path is always: sandbox bridge → ngrok → comet-mcp → CDP.
4. No chat-window polling; wake-up is via heartbeat/injection or user activation.
5. Per-role queues + busy leases prevent races.

## Related parent project

[grok-lisptc-MiS](https://github.com/MrJ55/grok-lisptc-MiS) — permanent mind, duties, P0–P12 surface.
