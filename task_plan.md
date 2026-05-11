# task_plan.md — Agent Wizard Active Plan

> Persistent planning file. Re-read before major decisions.

## Goal

Build a docs-first setup wizard that can later become a Claude Code plugin / skill pack / command system for generating repo-native agent operating systems.

## Current phase

Phase 0 — scaffold and methodology extraction.

## Done criteria for Phase 0

| # | Criterion | Status |
|---:|---|---|
| 1 | README defines north star, non-goals, command menu | done |
| 2 | CLAUDE.md defines repo operating instructions | done |
| 3 | AGENTS.md gives cold-start brief | done |
| 4 | planning files exist: task_plan / findings / progress | done |
| 5 | docs define project canon and wizard flow | done |
| 6 | docs extract planning-with-files methodology | done |
| 7 | docs extract Claude Agent SDK reusable patterns | done |
| 8 | numbered slash command stubs exist | done |
| 9 | ARC-NBA dogfood boundary documented | done |
| 10 | first Codex prompt delivered to operator | done |

## Phase 0 slices

| Slice | Output | Status |
|---|---|---|
| 0.1 | Root docs scaffold | done |
| 0.2 | Methodology extraction docs | done |
| 0.3 | Ordered command stubs | done |
| 0.4 | Dogfood / self-harness docs | done |
| 0.5 | First Codex prompt | done |

## Phase 1 preview

Implementation can start only after Phase 0 docs are reviewed.

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
| D2 | Install shape: plugin, skill pack, repo template, CLI, or hybrid | closed — Claude Code plugin containing 16 skills + agent orchestra + hooks, installed under `.claude/plugins/agent-wizard/` (locked 2026-05-11 via Group A grill Q4) |
| D3 | Default autonomy level | provisional L1 patch preview |
| D4 | Whether commands should use `/wizard:*` or `/agent-wizard:*` | provisional `/wizard:*` |
| D5 | How hard to enforce docs budget | open |
