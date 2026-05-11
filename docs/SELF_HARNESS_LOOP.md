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
