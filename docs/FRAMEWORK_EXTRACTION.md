# FRAMEWORK_EXTRACTION.md

## Purpose

Extract reusable framework, philosophy, and methodology from:

1. `OthmanAdi/planning-with-files`
2. official public Claude Agent SDK repos/docs

This doc is intentionally docs-only. It does not create implementation dependencies.

## 1. Planning with files — extracted framework

### Core thesis

Long-running agent work fails when everything lives in volatile context.

Therefore:

```text
context window = RAM
filesystem = disk
```

Agent Wizard should persist important state into files.

### Reusable artifacts

| Artifact | Role |
|---|---|
| `task_plan.md` | active plan, phases, done criteria |
| `findings.md` | research discoveries, source quirks |
| `progress.md` | session log, errors, tests, next actions |
| `decision_log.md` | irreversible decisions |
| `eval_rubric.md` | success criteria |
| `kill_gates.md` | stop conditions |

### Reusable rules

1. Create plan before complex work.
2. Re-read plan before major decisions.
3. Save findings after research.
4. Log errors and failed attempts.
5. Never repeat a failed action without changing approach.
6. Verify completion before stopping.
7. Use hooks for deterministic reminders.

## 2. Claude Agent SDK — extracted framework

### Public interface patterns

| SDK pattern | Agent Wizard mapping |
|---|---|
| `query()` one-shot mode | Wizard commands that run once and output a file |
| `ClaudeSDKClient` stateful mode | Long guided sessions / interactive setup |
| `ClaudeAgentOptions` | Generated project config |
| `allowed_tools` / `disallowed_tools` | Autonomy policy |
| `permission_mode` | Autonomy level |
| hooks | Harness and guardrails |
| custom tools / MCP servers | Future plugin integration |
| typed agent definitions | `.agent-wizard/orchestra.yaml` |

### Permission caveat

`allowed_tools` is not a sandbox by itself. It pre-approves matching tools; it does not prove that all other tools are structurally impossible under every permission mode.

Invalid state name: **allow-list-as-sandbox**.

Agent Wizard must model tool authority as:

```text
autonomy level
+ permission mode
+ allowed tools
+ disallowed tools
+ hooks / kill gates
```

If any part is missing, the generated setup is only labeled safe, not validated safe.

### Design lesson

Agent Wizard should separate:

1. one-shot commands,
2. interactive wizard session,
3. deterministic hooks,
4. tool permissions,
5. agent definitions,
6. target repo patches.

## 3. Combined philosophy

Agent Wizard = planning-with-files memory + SDK-style explicit interface contracts.

### Formula

```text
Repo scan
→ persistent docs
→ typed-ish project profile
→ ordered commands
→ agent orchestra
→ bounded permissions
→ deterministic hooks
→ eval loop
→ dogfood iteration
```

## 4. What not to copy

Do not copy source code blindly.

Extract principles:

- file-based memory,
- hook lifecycle,
- command contracts,
- typed options,
- explicit permissions,
- eval-first delivery.
