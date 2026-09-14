# Architecture — grok-mis-blackboard

## Layers

| Layer | Location | Authority |
|-------|----------|-----------|
| Mind (lisptc) | warm image in artifacts / parent MiS | Sole mutator of permanent identity |
| Blackboard | `artifacts/blackboard/` | Shared candidate + coordination state |
| Bridge | every live sandbox | Detection, queuing, ngrok client |
| Injection | ngrok → comet-mcp → CDP | Delivery only |
| Host / Orchestrator | primary Comet Grok tab | Constitutional decisions, promotions |
| Role agents | other tabs (own hot `/tmp/mis`) | Specialized contributions |

## Injection pipeline (only path)

```
MiS / role host
  → sandbox bridge (detect / enqueue)
  → ngrok
  → comet-mcp (local PC)
  → CDP
  → target Grok tab composer
```

comet-mcp has no access to artifacts. The sandbox bridge is the sensor and translator.

## Blackboard layout (target)

```
artifacts/blackboard/
├── state/           # goals, metrics, high-water marks, busy leases
├── tasks/           # open work items
├── claims/          # atomic claims
├── results/         # completed envelopes
├── receipts/        # seen / finished
├── queues/          # per-role injection queues
│   ├── orchestrator/
│   ├── generator-a/
│   └── ...
└── archive/         # compacted history
```

## Async principles

- No polling inside chat windows.
- Wake-up via Comet heartbeat / injection or user activation.
- File create / atomic claim = event.
- Per-role queues + busy leases prevent races across multi-stage workflows.
- Any live sandbox can detect a write and request an injection (bridge present everywhere).

## Safety

- Blackboard never becomes the executable image.
- Permanent changes still require MiS validate → eval → save-only-on-success.
- Reality-status and promote-candidate discipline unchanged.
- Bridge is I/O only; it does not evaluate Lisp or mutate identity.
