# findings.md — Agent Wizard Research Findings

> Store discoveries here before they become implementation.

## Source policy

Use only:

- official public Anthropic / Claude Code / Claude Agent SDK docs and repos,
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
