# findings.md — Agent Wizard Research Findings

> Store discoveries here before they become implementation.

## Source policy

Use only:

- official public Anthropic / Claude Agent SDK / Claude Code docs and repos,
- public community repos such as `OthmanAdi/planning-with-files`,
- this repo's own dogfood results,
- ARC-NBA as a dogfood target with explicit boundary.

Do not claim knowledge from unofficial or leaked Claude internals.

## Finding 1 — Planning with files pattern

`OthmanAdi/planning-with-files` defines a simple but powerful 3-file memory pattern:

```text
task_plan.md  → phases, status, decisions
findings.md   → research and discoveries
progress.md   → session log, test results, errors
```

Reusable mechanism for Agent Wizard:

1. Wizard setup must create persistent planning files.
2. Complex work should not live only in chat context.
3. Questions should map to files.
4. Errors should be logged so the agent does not repeat failures.
5. Hooks can remind the agent to re-read plan and update progress.

## Finding 2 — Filesystem as agent memory

The key idea is not the exact filenames. The reusable framework is:

```text
context window = volatile RAM
filesystem = durable project memory
```

Agent Wizard should install a memory spine into target repos instead of relying on a long initial prompt.

## Finding 3 — Claude Agent SDK interface discipline

The public Claude Agent SDK exposes several design patterns worth mapping into Agent Wizard docs:

1. `query()` is suitable for one-shot, stateless tasks.
2. `ClaudeSDKClient` is suitable for interactive, stateful conversations.
3. `ClaudeAgentOptions` centralizes configuration such as working directory, tool permission behavior, system prompt, hooks, and MCP servers.
4. Hooks provide deterministic control points outside the model.
5. Permission modes and tool allow/deny rules should be explicit, not implicit.
6. Agent definitions are typed around prompt, model, skills, tools, MCP servers, memory, max turns, background mode, effort, and permission mode.

Mapping to Agent Wizard:

- Every generated agent must have a typed-ish spec even in docs-only phase.
- Every autonomy claim must map to permission rules / allowed actions.
- Hooks are the correct place for deterministic guardrails.
- One-shot command flows and long-running agent flows should be designed separately.

## Finding 4 — Ordered commands beat clever commands for beginners

The operator wants numbered slash commands. This is correct for beginner completion because it creates visible progress and removes menu ambiguity.

Design implication:

```text
/wizard:01-start → /wizard:16-ship
```

Each command should:

1. state its prerequisite,
2. state its output artifact,
3. state stop conditions,
4. state what it refuses to modify.

## Finding 5 — Dogfood must be bidirectional

ARC-NBA is not just an example repo. It is the experiment target. But Agent Wizard must also dogfood itself.

Loop:

```text
Agent Wizard scans itself → diagnoses weak docs/gates → proposes patch → records learning → improves wizard commands
```

This prevents the wizard from becoming a pretty generator that cannot survive its own process.

## Finding 6 — Schema-bound interview beats open Q&A (methodology validation)

Source: Group A grill round, 2026-05-11.

The canonical 5-field block from `docs/GRILL_ME_WITH_DOCS.md` (`question / why_it_matters / answer_goes_to / affects_command / blocking_if_unanswered`) was applied to 5 product-canon questions in a single round.

Observed outcomes:

1. Surfaced 2 doc-level contradictions (C1 advisory-vs-enforced ARC-NBA rule; C2 dogfood signal omission) that an open Q&A would likely have missed, because each answer was forced to declare a target file and an affected command.
2. Closed 3 previously open product decisions in one round (primary user, install shape, done definition).
3. Produced a measurable doc edit plan with no ambiguity about where each anchor lives.

Design implication for `/wizard:03-grill`:

- The 5-field schema is **load-bearing**, not cosmetic. Drop any field and the round degrades.
- `answer_goes_to` is the single field that prevents anchor drift — every answer must name exactly one canonical file.
- `affects_command` is what catches advisory-vs-enforced contradictions early.
- `blocking_if_unanswered` distinguishes questions that gate Phase 1 from questions that can be deferred.

Validates the `/wizard:03-grill` design before any implementation work. The implementation must preserve the 5-field schema verbatim; deviation reopens the contradiction class this round just closed.

Voice tension to track (not a contradiction): Q2 promise frames "any working repo" (product positioning) while Q1 user is "AI beginner" (operator persona). Future doc voice must hold these distinct — positioning describes the product surface, persona describes who walks it.
