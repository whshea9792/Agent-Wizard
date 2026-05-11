# METHODOLOGY_MAP.md

## Goal

Map reusable methodology into Agent Wizard in a docs-only manner.

## Method stack

| Method | What we keep | Agent Wizard artifact |
|---|---|---|
| Planning with files | persistent memory files | `task_plan.md`, `findings.md`, `progress.md` |
| Claude Agent SDK | explicit options / permissions / hooks | `.agent-wizard/config.json`, autonomy docs |
| Ralph loop | goal → plan → act → observe → reflect | `docs/ITERATION_LOOP.md` |
| DSPy-inspired design | signatures, examples, eval metrics | `.agent-wizard/signatures.yaml`, eval rubric |
| GEPA-inspired design | reflect on failures, propose prompt patches | `docs/SELF_HARNESS_LOOP.md` |
| Grill me with docs | questions produce docs | `docs/GRILL_ME_WITH_DOCS.md` |

## Ralph loop mapping

```text
Goal → Plan → Act → Observe → Reflect → Patch → Commit → Learn
```

Agent Wizard mapping:

| Loop step | File |
|---|---|
| Goal | `docs/PROJECT_CANON.md` |
| Plan | `task_plan.md` |
| Act | command output |
| Observe | `progress.md` |
| Reflect | `findings.md` |
| Patch | proposed diff |
| Commit | PR plan |
| Learn | `docs/SELF_HARNESS_LOOP.md` |

## DSPy-inspired mapping

Do not require DSPy dependency at Phase 0.

Adopt the discipline:

```text
task signature + examples + metric + iteration
```

Candidate signatures:

```yaml
repo_scan:
  input: repo_path
  output: repo_profile
  metric: phase_detection_accuracy

question_generation:
  input: repo_profile
  output: question_set
  metric: artifact_mapping_coverage

persona_generation:
  input: project_profile
  output: persona_contract
  metric: hard_rule_completeness
```

## GEPA-inspired mapping

Use reflective evolution:

```text
run wizard → evaluate output → diagnose failure → propose instruction patch → run regression → accept/reject
```

No silent self-modification. All proposed evolution must be visible in diff.
