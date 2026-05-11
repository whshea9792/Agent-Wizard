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

## Command-level gates

These gates operationalise the §Behavioural refuses block in `docs/PROJECT_CANON.md`. They are enforcement, not advisory — each command listed below MUST check the gate before any write or external action.

### Gate 1 — Diff before install

**Command:** `/wizard:12-install`

**Trigger condition:** invoked without a fresh `/wizard:11-diff` artifact in session state, OR with a stale artifact (target file set changed since diff was produced).

**Required pre-state:**

- session state contains `last_diff_artifact_path` pointing to a readable file,
- the artifact's file list matches the install plan exactly,
- the artifact has not been invalidated by intervening writes.

**Refusal message:**

```text
status: refused
reason: /wizard:12-install requires a fresh /wizard:11-diff artifact. None found (or artifact is stale).
files_touched: none
safe_next_action: run /wizard:11-diff, review the diff, then re-run /wizard:12-install.
question_for_operator: do you want to run /wizard:11-diff now?
```

### Gate 2 — ARC-NBA mainline protection

**Command:** `/wizard:13-dogfood`

**Trigger condition:** target repo path resolves to ARC-NBA AND current target branch ∈ {`main`, `master`}.

**Required pre-state:**

- if target is ARC-NBA, the current branch must be a non-mainline branch (e.g. `dogfood/*`),
- write operations on ARC-NBA are refused regardless of branch unless operator explicitly approves with a project-specific autonomy override.

**Refusal message:**

```text
status: refused
reason: /wizard:13-dogfood cannot run against ARC-NBA mainline. ARC-NBA is a dogfood target, not a dependency, and mainline writes are blocked by CLAUDE.md Hard Rule 1.
files_touched: none
safe_next_action: check out a non-mainline branch in ARC-NBA (e.g. dogfood/<topic>), or change target to a different repo.
question_for_operator: which branch should the dogfood run target?
```

## Cross-references

- `docs/AUTONOMY_POLICY.md` §Invalid state — the "allow-list-as-sandbox" anti-pattern. A claim that `allowed_tools` alone makes a command safe is rejected here; Gate 1 and Gate 2 define the deny side that must accompany any allow.
- `CLAUDE.md` Hard Rule 1 — no ARC-NBA mainline writes. Gate 2 is the command-level enforcement of that rule.
- `CLAUDE.md` Hard Rule 6 — every wizard question maps to an artifact, command, or gate. Gates 1 and 2 are the destination for the two Q3 behavioural refuses.
