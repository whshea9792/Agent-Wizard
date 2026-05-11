# /wizard:01-start

## Purpose

Start a guided setup session.

## Prerequisites

- Read `README.md`.
- Read `task_plan.md`.
- Confirm current wizard phase.
- Do not skip earlier numbered steps unless operator explicitly says this is a targeted repair.

## Inputs

- Operator request.
- Existing Agent Wizard docs.
- Target repo context when applicable.

## Outputs

- Session brief.

## Procedure

1. State current step and prerequisite check.
2. Identify which artifact this command will update.
3. Perform only the minimum required action for this step.
4. Surface contradictions instead of hiding them.
5. Update `progress.md` or propose the update.

## Refusal conditions

Refuse or stop if:

- autonomy policy is missing for a risky action,
- target repo phase conflicts with requested work,
- command would skip required earlier setup,
- command would touch credentials, money, deploy, or trading execution,
- output artifact is unclear.

## Completion checklist

- [ ] Output artifact named.
- [ ] Operator-facing summary written.
- [ ] Next numbered command suggested.
