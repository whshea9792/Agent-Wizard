# task_plan.md — Agent Wizard Active Plan

> Persistent planning file. Re-read before major decisions.

## Goal

Build a docs-first Claude Code setup wizard that can later become a plugin / skill pack / command system for generating repo-native agent operating systems.

## Current phase

Phase 0 — scaffold and methodology extraction.

## Done criteria for Phase 0

| # | Criterion | Status |
|---:|---|---|
| 1 | README defines north star, non-goals, command menu | done |
| 2 | CLAUDE.md defines repo operating instructions | done |
| 3 | AGENTS.md gives cold-start brief | done |
| 4 | planning files exist: task_plan / findings / progress | in_progress |
| 5 | docs define project canon and wizard flow | pending |
| 6 | docs extract planning-with-files methodology | pending |
| 7 | docs extract Claude Agent SDK reusable patterns | pending |
| 8 | numbered slash command stubs exist | pending |
| 9 | ARC-NBA dogfood boundary documented | pending |
| 10 | first Claude Code prompt delivered to operator | pending |

## Phase 0 slices

| Slice | Output | Status |
|---|---|---|
| 0.1 | Root docs scaffold | in_progress |
| 0.2 | Methodology extraction docs | pending |
| 0.3 | Ordered command stubs | pending |
| 0.4 | Dogfood / self-harness docs | pending |
| 0.5 | First Claude Code prompt | pending |

## Phase 1 preview

Implementation can start only after Phase 0 docs are stable.

Likely Phase 1 slices:

1. Repo scanner POC.
2. Project profile schema.
3. Question engine.
4. Doc generator.
5. Command installer.
6. Doctor / drift checker.

## Open decisions

| ID | Decision | Status |
|---|---|---|
| D1 | Product name: Agent Wizard vs Agent Foundry Wizard | open |
| D2 | Install shape: plugin, skill pack, repo template, CLI, or hybrid | open |
| D3 | Default autonomy level | open |
| D4 | Whether commands should use `/wizard:*` or `/agent-wizard:*` | provisional `/wizard:*` |
| D5 | How hard to enforce docs budget | open |

## Next step

Finish Phase 0 scaffold on `main`, then grill operator with docs-first questions.
