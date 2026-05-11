# ITERATION_LOOP.md

## Ralph-loop inspired execution

Agent Wizard uses:

```text
Goal → Plan → Act → Observe → Reflect → Patch → Commit → Learn
```

## Mapping

| Step | Agent Wizard behavior |
|---|---|
| Goal | read project canon |
| Plan | update task_plan |
| Act | run numbered command |
| Observe | update progress |
| Reflect | update findings |
| Patch | show diff |
| Commit | PR plan |
| Learn | self-harness loop |

## Rule

The loop is not complete until learning is written to disk.
