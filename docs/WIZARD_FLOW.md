# WIZARD_FLOW.md

## Principle

Agent Wizard is completed step by step. Each step has a command, prerequisite, output artifact, and stop condition.

## Flow

| Step | Command | Prerequisite | Output | Stop condition |
|---:|---|---|---|---|
| 01 | `/wizard:01-start` | Repo exists | Session brief | Repo missing or no write plan |
| 02 | `/wizard:02-scan` | Start completed | Repo scan | Sensitive files detected |
| 03 | `/wizard:03-grill` | Scan completed | Question log | Operator says pause |
| 04 | `/wizard:04-profile` | Grill answers | Project profile | Contradiction unresolved |
| 05 | `/wizard:05-design` | Profile | Persona/workflow design | Autonomy unclear |
| 06 | `/wizard:06-orchestra` | Design | Agent team spec | Role overlap unresolved |
| 07 | `/wizard:07-commands` | Orchestra | Command menu | Commands not ordered |
| 08 | `/wizard:08-harness` | Commands | Harness plan | No deterministic checks |
| 09 | `/wizard:09-eval` | Harness | Eval rubric | No measurable criteria |
| 10 | `/wizard:10-autonomy` | Eval | Autonomy policy | No kill gates |
| 11 | `/wizard:11-diff` | Policy | Proposed patch | Diff too wide |
| 12 | `/wizard:12-install` | Approved diff | Files installed | User rejects diff |
| 13 | `/wizard:13-dogfood` | Installed wizard | Dogfood report | Target repo phase conflict |
| 14 | `/wizard:14-iterate` | Dogfood report | Improvement plan | Regression risk unclear |
| 15 | `/wizard:15-doctor` | Any time | Drift report | Critical contradiction found |
| 16 | `/wizard:16-ship` | Green doctor | PR/release plan | Acceptance missing |

## Anti-pattern

Do not let `/wizard:03-grill` become endless conversation. Each question must update a named artifact.
