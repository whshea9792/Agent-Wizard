# First prompt to Codex — Agent Wizard scaffold

You are Codex working inside `whshea9792/Agent-Wizard`.

## Mission

Initialize and refine a docs-first scaffold for **Agent Wizard**: a step-by-step setup wizard that generates repo-native agent operating systems for Claude Code / Codex projects.

This is not an ARC-NBA feature. ARC-NBA is only a dogfood target.

## Immediate task

Apply the scaffold from the provided zip into the repo root.

Expected root files:

```text
README.md
CLAUDE.md
AGENTS.md
task_plan.md
findings.md
progress.md
```

Expected docs:

```text
docs/PROJECT_CANON.md
docs/GRILL_ME_WITH_DOCS.md
docs/WIZARD_FLOW.md
docs/COMMAND_MENU.md
docs/FRAMEWORK_EXTRACTION.md
docs/METHODOLOGY_MAP.md
docs/AUTONOMY_POLICY.md
docs/KILL_GATES.md
docs/EVAL_RUBRIC.md
docs/ARTIFACT_CONTRACT.md
docs/REPO_SCANNER_SPEC.md
docs/PERSONA_CONTRACT_TEMPLATE.md
docs/ORCHESTRA_SPEC.md
docs/HARNESS_SPEC.md
docs/SELF_HARNESS_LOOP.md
docs/DOGFOOD_ARC_NBA.md
docs/ITERATION_LOOP.md
```

Expected command stubs:

```text
.claude/commands/wizard-01-start.md
.claude/commands/wizard-02-scan.md
.claude/commands/wizard-03-grill.md
.claude/commands/wizard-04-profile.md
.claude/commands/wizard-05-design.md
.claude/commands/wizard-06-orchestra.md
.claude/commands/wizard-07-commands.md
.claude/commands/wizard-08-harness.md
.claude/commands/wizard-09-eval.md
.claude/commands/wizard-10-autonomy.md
.claude/commands/wizard-11-diff.md
.claude/commands/wizard-12-install.md
.claude/commands/wizard-13-dogfood.md
.claude/commands/wizard-14-iterate.md
.claude/commands/wizard-15-doctor.md
.claude/commands/wizard-16-ship.md
```

Expected config:

```text
.agent-wizard/config.json
.agent-wizard/orchestra.yaml
.agent-wizard/signatures.yaml
```

## Research basis

Use these public sources as design inspiration only:

1. `OthmanAdi/planning-with-files`
   - extract file-based planning, persistent memory, progress tracking, and hook discipline.
2. Official Anthropic Claude Agent SDK public repo/docs
   - extract explicit options, permission mode, allowed/disallowed tools, hooks, typed agent definitions, one-shot vs stateful sessions.

Do not copy private or unofficial Claude Code internals.

## Hard rules

1. Keep this PR docs-only. No implementation code yet.
2. Slash commands must remain ordered from `/wizard:01-start` to `/wizard:16-ship`.
3. Every command must state prerequisites, outputs, refusal conditions, and completion checklist.
4. ARC-NBA is dogfood only. Do not modify ARC-NBA.
5. Autopilot must be bounded by explicit autonomy levels and kill gates.
6. No new dependency.
7. One PR equals one vertical slice.

## After applying files

Run:

```bash
git status
find . -maxdepth 3 -type f | sort
```

Then inspect the scaffold and improve only obvious docs inconsistencies. Do not add implementation code.

## Commit

Commit message:

```text
docs: scaffold Agent Wizard docs-first setup flow
```

## Final response

Return:

1. files created/updated,
2. any deviations,
3. next recommended PR,
4. first five `Grill Me With Docs` questions for the operator.
