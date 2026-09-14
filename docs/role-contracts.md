# Role Contracts

| Role | Inductive bias | May write | May promote permanent image |
|------|----------------|-----------|-----------------------------|
| Orchestrator (Host) | Constitutional, duty-driven | tasks, state, promotions | **Yes** (sole) |
| Generator | DMN-like, incomplete hypotheses | hypotheses / tasks for Analyst | No |
| Analyst | TPN-like, well-formed Lisp | proposals (candidates) | No |
| Critic | Multi-criteria scoring | evaluations / reflections | No |
| Mutator | Meta, chromosomes | mutation suggestions | No |

## Common rules

- All writes use the blackboard schema.
- Claims are atomic.
- Results carry fitness vectors when applicable.
- No role except Orchestrator/Host may call MiS `--save` on identity-changing forms.
- Role-specific custom instructions / system prompts enforce the inductive bias.

## Parallelism

Multiple Generator instances (A/B) or heterogeneous model families are encouraged for diversity. Orchestrator may require contributions from ≥2 sources before a promote cycle.
