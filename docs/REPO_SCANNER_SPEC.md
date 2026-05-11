# REPO_SCANNER_SPEC.md

## Purpose

Define what `/wizard:02-scan` should inspect.

## Must read

- `README.md`
- `CLAUDE.md`
- `AGENTS.md`
- `task_plan.md`
- package files: `pyproject.toml`, `package.json`, etc.
- `.github/workflows/`
- `.claude/`
- top-level docs
- recent git log
- open PRs if available

## Must avoid

- secrets
- `.env`
- private keys
- large binary files
- vendor caches
- data dumps

## Output

`docs/generated/REPO_SCAN.md` or `.agent-wizard/repo_scan.json`

## Classifications

The scanner should classify:

1. repo purpose,
2. active phase,
3. docs maturity,
4. test maturity,
5. automation maturity,
6. autonomy risk,
7. install readiness.
