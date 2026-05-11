# PROJECT_CANON.md

## Product

Agent Wizard is a setup wizard for creating repo-native agent operating systems.

Install shape: Claude Code plugin containing 16 skills + agent orchestra + hooks. Installed under `.claude/plugins/agent-wizard/` in the target repo.

## Primary user

AI beginner. The operator can read docs and run slash commands, but is not expected to debug agent internals, write hook scripts, or hand-author persona contracts.

The wizard must therefore be completable end-to-end without external help — `/wizard:01-start` through `/wizard:16-ship` must succeed using only the artifacts the wizard itself generates.

## Core promise

Docs-first 將任何 working repo 轉成有 gates、有 orchestra 嘅 agent 系統。

Concretely, the wizard turns vague intent into a structured setup process:

1. scan the repo,
2. ask alignment questions,
3. write project docs,
4. design persona and agents,
5. generate ordered commands,
6. define autonomy gates,
7. define harness and eval loops,
8. propose install diff.

## Non-goals

- Do not auto-install into a target repo before showing a diff.
- Do not treat autopilot as unlimited authority.
- Do not mix ARC-NBA product work into Agent Wizard.
- Do not depend on private or unofficial Claude internals.
- Do not create docs that have no command, artifact, or gate attached.

## Behavioural refuses

The wizard must refuse, at command level (enforcement in `docs/KILL_GATES.md`):

- Refuse to run `/wizard:12-install` if no `/wizard:11-diff` artifact exists in session state. Diff preview is mandatory before any write.
- Refuse to run `/wizard:13-dogfood` against ARC-NBA mainline (`main` or `master`). ARC-NBA dogfood is read-only or branch-scoped only.

## Product law

Every wizard question must produce one of:

- a document section,
- a command behavior,
- a generated file,
- an autonomy rule,
- a kill gate,
- an eval case.

If a question produces none of those, remove it.

## Done definition

Agent Wizard is "done enough to ship Phase 1" when all three signals hold:

1. **Beginner completion.** A fresh AI-beginner operator walks `/wizard:01-start` → `/wizard:16-ship` without needing AI clarifications outside the command bodies themselves.
2. **Full artifact set.** All 10 North Star artifacts exist in the target repo at end of run: project canon, persona contract, numbered slash commands, agent orchestra, autonomy policy, kill gates, harness checks, evaluation rubric, dogfood loop, PR plan.
3. **One closed dogfood loop.** The operator runs `/wizard:13-dogfood` at least once and the result lands as a recorded learning in `findings.md` (scan → finding → patch proposal → recorded learning).

Measurable pass/fail rules live in `docs/EVAL_RUBRIC.md`.
