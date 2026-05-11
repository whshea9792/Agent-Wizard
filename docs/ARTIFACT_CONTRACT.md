# ARTIFACT_CONTRACT.md

## Purpose

Prevent document sprawl.

## Mandatory artifacts

| File | Purpose |
|---|---|
| `README.md` | product entrypoint |
| `CLAUDE.md` | repo-level operating instructions |
| `AGENTS.md` | cold-start brief |
| `task_plan.md` | current plan |
| `findings.md` | research notes |
| `progress.md` | session log |
| `docs/PROJECT_CANON.md` | project truth |
| `docs/AUTONOMY_POLICY.md` | allowed actions |
| `docs/KILL_GATES.md` | stop rules |
| `docs/EVAL_RUBRIC.md` | quality bar |
| `.claude/commands/*.md` | wizard menu |

## Artifact frontmatter

Future docs should use:

```yaml
---
status: draft
owner: agent-wizard
last_updated: YYYY-MM-DD
revisit_trigger: command/phase change
---
```

## Deletion rule

If a doc is not referenced by any command, artifact, or gate, delete or merge it.
