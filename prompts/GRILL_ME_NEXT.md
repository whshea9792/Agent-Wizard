# Grill Me With Docs — next operator questions

> Group A (5 product-canon questions) resolved 2026-05-11.
> Remaining items here = autonomy default + dogfood ordering + install-write detail.
> See `docs/PROJECT_CANON.md` (anchors) and `docs/KILL_GATES.md` (Q3 enforcement) for the resolved decisions.

Ask these in the next grill round.

## 1. Default autonomy

Confirm or change the default autonomy level. The scaffold currently uses L1 patch preview.

A. Keep L1 patch preview
B. Downgrade to L0 advisory
C. L2 local write
D. L3 commit-gated
E. L4 PR autopilot

Answer goes to: `docs/AUTONOMY_POLICY.md`

## 2. First dogfood

Which comes first?

A. Agent Wizard scans itself
B. Agent Wizard scans ARC-NBA
C. Both, but self first

Answer goes to: `docs/SELF_HARNESS_LOOP.md`

## 3. Install behavior

Should `/wizard:12-install` directly write files after approval, or always create a patch file first?

Answer goes to: `docs/WIZARD_FLOW.md` and `docs/AUTONOMY_POLICY.md`

Note: Gate 1 in `docs/KILL_GATES.md` already mandates a fresh `/wizard:11-diff` artifact before any install. This question is about what happens **after** the gate passes — direct write vs. patch-file intermediary.
