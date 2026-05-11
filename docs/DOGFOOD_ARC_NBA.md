# DOGFOOD_ARC_NBA.md

## Purpose

Define how Agent Wizard uses ARC-NBA as a dogfood target.

## Boundary

ARC-NBA is not part of Agent Wizard. It is a target repo for testing the wizard.

## What Agent Wizard may do

- scan ARC-NBA docs,
- detect current phase,
- propose setup improvements,
- generate a dogfood report,
- learn from ARC-NBA's persona / planning / harness patterns.

## What Agent Wizard must not do by default

- modify ARC-NBA mainline,
- create ARC-NBA PRs,
- change ARC-NBA product roadmap,
- bypass ARC-NBA phase plan,
- touch betting/trading execution.

## Report output

`docs/dogfood/arc-nba-report.md`

## Learning output

`findings.md` section: `ARC-NBA dogfood findings`
