# HARNESS_SPEC.md

## Purpose

Define deterministic guardrails for Agent Wizard and target repos.

## Candidate hooks

| Hook | Purpose |
|---|---|
| SessionStart | inject active plan and command status |
| UserPromptSubmit | detect override phrases / unsafe requests |
| PreToolUse | block destructive actions |
| PostToolUse | remind progress update |
| Stop | verify completion checklist |
| SubagentStop | collect subagent output |

## Deterministic checks

- command order check,
- required artifact check,
- autonomy policy check,
- kill gate check,
- docs reference check,
- no secrets in generated files,
- target repo boundary check.

## Phase 0 stance

Docs only. Do not implement hooks yet.
