# SELF_HARNESS_LOOP.md

## Purpose

Agent Wizard must improve itself using its own wizard process.

## Loop

```text
scan Agent Wizard
→ generate repo profile
→ run doctor
→ identify weak docs / missing gates
→ propose patch
→ evaluate with rubric
→ update methodology
```

## Dogfood target #0

Agent Wizard itself.

## Dogfood target #1

ARC-NBA.

ARC-NBA must remain separate. Any ARC-NBA dogfood output is a report unless the operator explicitly requests a patch.

## Iteration rule

No silent self-modification. Every self-improvement must be visible as a diff or PR.

## Closed dogfood loop — definition

A dogfood run is "closed" only when all four stages complete and are recorded:

1. **Scan** — `/wizard:13-dogfood` runs against the chosen target (Agent Wizard itself or an allowed ARC-NBA branch) and produces a scan observation.
2. **Finding** — the observation is converted into a named finding (weak doc, missing gate, contradiction, drift) and logged in `findings.md`.
3. **Patch proposal** — a concrete change is proposed: either a doc edit, a command refinement, a new gate, or a rubric update. The proposal is captured as a planned diff (not yet installed).
4. **Recorded learning** — the loop closes with a dated entry in `findings.md` or `progress.md` that names what changed in the wizard methodology as a result. A scan that produced no finding still counts as a closed loop iff the null result is recorded.

A run that stops at stage 1 or 2 is **open**, not closed. Open runs do not count toward Phase 1 ship signals.

This definition is the measurement target for `docs/EVAL_RUBRIC.md` §Signal 3.
