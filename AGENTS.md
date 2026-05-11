# AGENTS.md — Agent Wizard Cold-Start Brief

> Target: any Codex / Claude Code session can read this file and understand the repo in under 3 minutes.

## 1. Identity

Agent Wizard is a setup wizard for generating repo-native agent operating systems.

It turns:

```text
fuzzy idea + working repo + operator answers
```

into:

```text
project canon + persona contract + ordered commands + agent orchestra + autonomy policy + harness + eval loop
```

## 2. Current phase

Phase 0: docs-first scaffold.

No implementation code yet. Build understanding first.

## 3. Read order

1. `README.md`
2. `CLAUDE.md`
3. `task_plan.md`
4. `docs/PROJECT_CANON.md`
5. `docs/WIZARD_FLOW.md`
6. `docs/COMMAND_MENU.md`
7. `progress.md`

## 4. Default command family

Commands must be ordered:

```text
/wizard:01-start
/wizard:02-scan
/wizard:03-grill
/wizard:04-profile
/wizard:05-design
/wizard:06-orchestra
/wizard:07-commands
/wizard:08-harness
/wizard:09-eval
/wizard:10-autonomy
/wizard:11-diff
/wizard:12-install
/wizard:13-dogfood
/wizard:14-iterate
/wizard:15-doctor
/wizard:16-ship
```

## 5. Core methodology

Agent Wizard combines four reusable methods:

1. **Planning with files** — filesystem as persistent memory: `task_plan.md`, `findings.md`, `progress.md`.
2. **Claude Agent SDK interface discipline** — explicit options, permissions, hooks, typed agent definitions, one-shot vs stateful mode distinction.
3. **Grill me with docs** — every question must map to a document, artifact, or command behavior.
4. **Dogfood harness loop** — the wizard must scan and improve itself before claiming it can improve other repos.

## 6. Non-negotiables

- Ordered beginner-completable steps.
- Bounded autonomy, never vague autopilot.
- Docs before code.
- ARC-NBA is dogfood only.
- Every output artifact must have a reason to exist.
- No hidden reliance on unofficial internals.

## 7. First useful task

Create or improve docs that answer:

1. What does the wizard ask?
2. What does each answer produce?
3. What files does it install?
4. What commands does it expose?
5. What does it refuse to do?
6. How does it evaluate itself?
