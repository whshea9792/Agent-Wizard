# COMMAND_MENU.md

## Rule

All slash commands must be numbered.

Numbering creates a visible wizard path and removes ambiguity for beginners.

## Command contract

Each command file must include:

```md
# /wizard:NN-name

## Purpose
## Prerequisites
## Inputs
## Outputs
## Procedure
## Refusal conditions
## Completion checklist
```

## Command list

1. `/wizard:01-start`
2. `/wizard:02-scan`
3. `/wizard:03-grill`
4. `/wizard:04-profile`
5. `/wizard:05-design`
6. `/wizard:06-orchestra`
7. `/wizard:07-commands`
8. `/wizard:08-harness`
9. `/wizard:09-eval`
10. `/wizard:10-autonomy`
11. `/wizard:11-diff`
12. `/wizard:12-install`
13. `/wizard:13-dogfood`
14. `/wizard:14-iterate`
15. `/wizard:15-doctor`
16. `/wizard:16-ship`

## Naming decision

Use `/wizard:*` for beginner ergonomics. If collision happens later, rename to `/agent-wizard:*`.
