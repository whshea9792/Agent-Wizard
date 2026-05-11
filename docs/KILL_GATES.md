# KILL_GATES.md

## Purpose

Define conditions that stop the wizard before damage compounds.

## Global kill gates

Stop immediately if:

1. target repo phase conflicts with requested work,
2. secrets or credentials are detected in proposed diff,
3. install diff touches files outside allowed paths,
4. command order is broken,
5. autonomy policy is missing,
6. generated persona contradicts project canon,
7. target repo has no rollback path,
8. the wizard cannot explain why a generated file exists,
9. dogfood report shows regression without mitigation,
10. operator says stop.

## Stop output

When stopped, output:

```text
status:
reason:
files_touched:
safe_next_action:
question_for_operator:
```
