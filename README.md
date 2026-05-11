# Agent Wizard

> Claude Code / Codex setup wizard for building repo-native agent operating systems from ground 0: idea → POC → prototype → MVP → end product → north-star expansion.

Agent Wizard is not a generic prompt pack. It is a docs-first, harness-first setup wizard that scans a working repo, grills the operator with structured questions, and generates a tailored agent operating system for that repo.

## North Star

Build a **step-by-step setup wizard** that helps a beginner operator create a production-grade project agent with:

1. a clear project canon,
2. a repo-native persona contract,
3. ordered slash-command menu,
4. subagent orchestra,
5. bounded autonomy policy,
6. harness checks,
7. research / iteration loop,
8. dogfood feedback loop.

The wizard should make fuzzy ideas executable without pretending that unlimited autonomy is safe.

## What this repo is

A future Claude Code plugin / skill pack / command system that can be installed into a target repo and guide the operator through numbered steps.

The first dogfood target is `whshea9792/ARC-NBA`, but ARC-NBA remains a separate product repo. Agent Wizard uses ARC-NBA as an experiment target and learns back from that experiment.

## What this repo is not

- Not a betting bot.
- Not an ARC-NBA feature branch.
- Not a one-shot `CLAUDE.md` generator.
- Not a replacement for human judgment.
- Not an excuse to auto-merge, auto-deploy, or auto-spend money without explicit gates.
- Not a wrapper around leaked or unofficial Claude Code internals. This repo studies official public SDK/docs and public community planning patterns only.

## Wizard command menu

The slash commands are intentionally ordered so a beginner can complete the wizard step by step.

| Order | Command | Purpose |
|---:|---|---|
| 01 | `/wizard:01-start` | Start a guided setup session |
| 02 | `/wizard:02-scan` | Scan the working repo |
| 03 | `/wizard:03-grill` | Ask docs-first alignment questions |
| 04 | `/wizard:04-profile` | Produce project profile |
| 05 | `/wizard:05-design` | Design persona + workflow |
| 06 | `/wizard:06-orchestra` | Design subagent orchestra |
| 07 | `/wizard:07-commands` | Generate slash command menu |
| 08 | `/wizard:08-harness` | Generate harness / guardrail plan |
| 09 | `/wizard:09-eval` | Generate eval rubric / regression cases |
| 10 | `/wizard:10-autonomy` | Set autonomy levels and kill gates |
| 11 | `/wizard:11-diff` | Show proposed target-repo patch |
| 12 | `/wizard:12-install` | Install approved files into target repo |
| 13 | `/wizard:13-dogfood` | Run against ARC-NBA or another target |
| 14 | `/wizard:14-iterate` | Improve the wizard from dogfood results |
| 15 | `/wizard:15-doctor` | Check drift, contradictions, missing gates |
| 16 | `/wizard:16-ship` | Prepare PR plan / release slice |

## Current phase

**Phase 0 — Docs-first scaffold.**

No implementation code yet. The job now is to define the product, wizard flow, artifacts, and acceptance criteria tightly enough that Codex / Claude Code can implement without guessing.

## Reading order

1. `README.md`
2. `CLAUDE.md`
3. `AGENTS.md`
4. `task_plan.md`
5. `docs/PROJECT_CANON.md`
6. `docs/WIZARD_FLOW.md`
7. `docs/FRAMEWORK_EXTRACTION.md`
8. `docs/METHODOLOGY_MAP.md`
9. `docs/COMMAND_MENU.md`
10. `docs/SELF_HARNESS_LOOP.md`

## Default development shape

One PR = one vertical slice.

Recommended early PRs:

1. PR1 — docs scaffold + project canon.
2. PR2 — numbered slash command files.
3. PR3 — repo scanner spec + project profile schema.
4. PR4 — persona/orchestra generator spec.
5. PR5 — harness/eval/autonomy spec.

## Dogfood principle

Agent Wizard must be able to inspect its own repo and improve itself. This creates a self-harness loop:

> Wizard scans Agent Wizard → finds missing docs / weak gates → proposes patch → evals itself → records learning → updates command behavior.

ARC-NBA is dogfood target #1. Agent Wizard itself is dogfood target #0.
