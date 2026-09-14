# Session handoff — grok-mis-blackboard

## Identity

You are operating in the multi-agent blackboard layer that sits on top of grok-lisptc-MiS.

## Bootstrap

1. Read WIKI.md, plan/README.md, docs/architecture.md.
2. Confirm parent MiS mind is available (or bootstrap it).
3. Ensure `artifacts/blackboard/` layout exists (create if missing).
4. Start / verify the sandbox bridge component (watcher + queue + ngrok client).
5. Check current high-water marks and any pending queues.

## Turn protocol

1. State intent in plain English.
2. If acting as Orchestrator: scan blackboard, update state, emit tasks or promotions as needed.
3. If acting as a specialized role: claim work if present, produce result envelope, write receipt.
4. Any blackboard write that should wake another role must go through the bridge so an injection can be requested.
5. Permanent mind changes still use the MiS bridge with --save only on success.

## Do not

- Poll the blackboard in a tight loop inside the chat.
- Let comet-mcp read artifacts directly.
- Auto-promote candidates into the permanent image.
- Skip high duties or silent-ignore injected proposals.

## Pins

Parent: https://github.com/MrJ55/grok-lisptc-MiS  
This layer: https://github.com/MrJ55/grok-mis-blackboard
