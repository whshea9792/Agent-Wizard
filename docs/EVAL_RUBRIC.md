# EVAL_RUBRIC.md

## Purpose

Define how to judge whether Agent Wizard output is good.

## Minimum rubric

| Area | Pass condition |
|---|---|
| Beginner completion | Commands are numbered and stepwise |
| Artifact quality | Every file has purpose and owner |
| Autonomy safety | Policy and kill gates exist |
| Repo fit | Profile reflects actual repo phase |
| Persona clarity | Agent authority and refusal rules are explicit |
| Harness | Deterministic checks are specified |
| Eval loop | Regression cases exist |
| Dogfood | Agent Wizard can run against itself |

## Red flags

- Generates many docs without command mapping.
- Uses vague agent roles like “do everything assistant”.
- Claims autopilot without permission boundaries.
- Installs files without diff preview.
- Treats ARC-NBA as a dependency.
- Adds dependencies before plain-file prototype.
