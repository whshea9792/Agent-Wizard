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

## Done definition — Phase 1 ship signals

Maps the three Q5 acceptance signals from `docs/PROJECT_CANON.md` §Done definition into pass/fail rules. All three must pass.

### Signal 1 — Beginner completion (binary)

**Pass condition:** a fresh AI-beginner operator completes `/wizard:01-start` → `/wizard:16-ship` with **zero AI clarification turns outside the command bodies themselves**.

- Each `/wizard:NN-*` command's own prompts, questions, and stop conditions count as in-body and are allowed.
- Any operator question that requires an external chat reply (e.g. "what does this step mean?", "what do I type?") counts as a failure.
- Measured by transcript inspection of one dogfood run, not by self-report.

**Fail signal:** transcript shows ≥1 clarification turn outside a command body.

### Signal 2 — Full artifact set (file-existence + size-sanity)

**Pass condition:** at end of run, target repo contains all 10 North Star artifacts. Each file must exist AND be non-trivially populated (size sanity: ≥ a minimum byte/line floor and contains the expected canonical section headers).

| # | Artifact | Path (target repo) | Minimum |
|---:|---|---|---|
| 1 | Project canon | `docs/PROJECT_CANON.md` | §Product, §Primary user, §Core promise present |
| 2 | Persona contract | `docs/PERSONA_CONTRACT.md` | role, authority, refusals defined |
| 3 | Numbered slash commands | `.claude/plugins/agent-wizard/commands/wizard-01..16-*` | all 16 files exist |
| 4 | Agent orchestra | `docs/ORCHESTRA_SPEC.md` | ≥1 agent role defined with prompt + tools |
| 5 | Autonomy policy | `docs/AUTONOMY_POLICY.md` | default level + hard locks |
| 6 | Kill gates | `docs/KILL_GATES.md` | ≥2 command-level gates with refusal messages |
| 7 | Harness checks | `docs/HARNESS_SPEC.md` | ≥1 deterministic check defined |
| 8 | Evaluation rubric | `docs/EVAL_RUBRIC.md` | this document |
| 9 | Dogfood loop | `docs/SELF_HARNESS_LOOP.md` | closed-loop definition present |
| 10 | PR plan | `docs/PR_PLAN.md` or equivalent in `task_plan.md` | one-PR-per-slice rule encoded |

**Fail signal:** any artifact missing, empty, or lacks required section.

### Signal 3 — One closed dogfood loop (recorded learning)

**Pass condition:** `findings.md` contains at least one entry that:

1. originated from a `/wizard:13-dogfood` run (entry references the command and target),
2. follows the full loop: scan observation → identified finding → patch proposal → recorded learning,
3. is dated and traceable to a session in `progress.md`.

**Fail signal:** `findings.md` has no `/wizard:13-dogfood`-sourced entry, or an entry exists but skips a loop stage.

See `docs/SELF_HARNESS_LOOP.md` for the canonical definition of a closed loop.
