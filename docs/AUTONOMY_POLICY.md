# AUTONOMY_POLICY.md

## Principle

Autopilot means bounded authority, not unlimited action.

An autonomy label is not enforcement. Each level must map to concrete permission mode, allowed tools, disallowed tools, and hook / kill-gate behavior before it can be installed.

## Autonomy levels

| Level | Name | Authority |
|---:|---|---|
| L0 | Advisory | Analyze only, no writes |
| L1 | Patch preview | Propose files/diff, no writes |
| L2 | Local write | Write local files, no commit |
| L3 | Commit-gated | Commit locally, no push |
| L4 | PR autopilot | Branch, commit, push, open PR |
| L5 | Production autopilot | Merge/deploy/external actions; requires explicit project-specific promotion |

## Default

Default for Agent Wizard target repos: **L1 Patch preview**.

The wizard may propose a patch but should not install it unless the operator explicitly approves `/wizard:12-install`.

This default is provisional. A target repo may downgrade to L0 for read-only review or promote to L2+ only after the operator accepts the specific authority increase.

## Hard locks

The wizard must not touch:

- credentials,
- paid API usage,
- money movement,
- trading / betting execution,
- production deploy,
- legal/tax filing,
- destructive repo settings,

unless a project-specific autonomy file explicitly permits it.

## Invalid state

Name: **allow-list-as-sandbox**.

This occurs when a generated setup claims safety because `allowed_tools` is present, but does not also define deny rules, permission mode, and deterministic hooks for blocked actions.
