# PROJECT_CANON.md

## Product

Agent Wizard is a setup wizard for creating repo-native agent operating systems.

## Primary user

A beginner AI operator who wants Codex / Claude Code to help turn abstract ideas into working projects without losing control of direction, scope, or safety.

## Core promise

Agent Wizard turns vague intent into a structured setup process:

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

## Product law

Every wizard question must produce one of:

- a document section,
- a command behavior,
- a generated file,
- an autonomy rule,
- a kill gate,
- an eval case.

If a question produces none of those, remove it.
