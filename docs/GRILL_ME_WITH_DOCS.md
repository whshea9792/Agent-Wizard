# GRILL_ME_WITH_DOCS.md

## Purpose

The wizard asks hard alignment questions until the operator and agent share a precise understanding.

This is not casual brainstorming. Every question must map to an artifact.

## Question rule

Each question must declare:

```text
question:
why_it_matters:
answer_goes_to:
affects_command:
blocking_if_unanswered:
```

## Core question groups

### A. Product canon

1. Who is the wizard for?
2. What is the one-sentence promise?
3. What must it refuse to do?
4. Is this a plugin, skill pack, repo template, CLI, or hybrid?
5. What does “done” look like for a first-time beginner?

Output: `docs/PROJECT_CANON.md`

### B. Autonomy

1. Can it write files?
2. Can it commit?
3. Can it push?
4. Can it open PRs?
5. Can it merge?
6. Can it call paid APIs?
7. Can it touch credentials?
8. Which domains are hard-locked by default?

Output: `docs/AUTONOMY_POLICY.md`, `docs/KILL_GATES.md`

### C. Repo scanner

1. What files must it always read?
2. What files must it never read?
3. Should it read git log?
4. Should it read open PRs?
5. Should it classify project phase?

Output: `docs/REPO_SCANNER_SPEC.md`

### D. Persona and orchestra

1. Should default agent be architect, PM, operator coach, or reviewer?
2. What subagents are allowed?
3. Which agent has final say?
4. What role overlap is forbidden?

Output: `docs/PERSONA_CONTRACT_TEMPLATE.md`, `docs/ORCHESTRA_SPEC.md`

### E. Evaluation

1. How do we know the generated setup is good?
2. What are the regression cases?
3. What is the minimum artifact set?
4. What failures should block install?

Output: `docs/EVAL_RUBRIC.md`
