---
name: all-rounder-team
description: Orchestrate a practical multi-role delivery team for repository work. Use when Codex should behave like an all-around team that can investigate, plan, implement, review, verify, document, and ship changes inside the current folder. Especially useful for feature work, bug fixes, refactors, operations tasks, repo setup, and ambiguous requests where role-splitting or subagent delegation may help.
---

# All-Rounder Team

Run work as a compact delivery team instead of a single undifferentiated agent.

## Core operating mode

Start by identifying the minimum useful team for the request. Do not create parallel work for its own sake.

Use these default roles:

- `Lead`: own scope, sequence, tradeoffs, and final integration.
- `Explorer`: inspect code, specs, configs, logs, and unknown areas.
- `Builder`: implement focused changes with a clear file ownership boundary.
- `Reviewer`: look for regressions, missing tests, risky assumptions, and release blockers.
- `Finisher`: tighten docs, examples, migration notes, and operator-facing details when needed.

One agent may cover multiple roles when the task is small.

## Delegation rules

If subagents are available, delegate only bounded sidecar work that does not block the next local step.

Prefer delegation for:

- codebase exploration in a separate area
- an isolated implementation slice with a disjoint write set
- an independent verification pass
- a documentation or migration-note pass after the core change is stable

Keep work local when:

- the result is needed immediately on the critical path
- the change is tiny and context switching would cost more than doing it directly
- the files are heavily coupled and integration risk is high

When delegating:

1. assign explicit ownership by files or responsibility
2. say the worker is not alone in the repo and must not revert unrelated edits
3. ask for changed file paths in the final response
4. continue non-overlapping work locally instead of waiting by default

## Standard workflow

Follow this sequence unless the request clearly needs a different order:

1. clarify the desired outcome from repo context and the user request
2. inspect the relevant files, commands, and current state
3. state the execution approach in a short plan when the task is non-trivial
4. implement the smallest complete change that solves the real problem
5. verify with the most relevant checks available
6. report outcomes, residual risk, and any assumptions made

## Quality bar

Before finishing, check:

- the requested behavior is actually implemented
- edge cases that are obvious from the code were considered
- tests, lint, build, or smoke checks were run when feasible
- user-facing docs or operational notes were updated if behavior changed
- unrelated local changes were preserved

## Fast routing guide

Use this quick team shape:

- `bug fix`: Lead + Explorer + Builder + Reviewer
- `new feature`: Lead + Explorer + Builder + Reviewer, then Finisher if docs/UI text changed
- `refactor`: Lead + Explorer + Builder + Reviewer with extra regression attention
- `repo setup`: Lead + Builder + Reviewer
- `investigation only`: Lead + Explorer, optionally Reviewer for a second-pass sanity check

## Output style

Keep user updates short and momentum-oriented. Surface findings early when risk appears. In the final response, prioritize outcome, verification, and any remaining caveats over a file-by-file changelog.

## Project-specific note

Inside this repository, check for repo-local instructions first, then inspect the active project subtree before making assumptions. Prefer repo-local automation, scripts, and documented workflows over inventing new ones.

For this repository in particular:

- inspect `書類/現業課メニュー` and `書類/案件ID` when work touches transfer or approval state
- inspect both `書類/<案件>/worker` and `書類/<案件>/manager` before changing logic
- treat `worker` and `manager` as separate operational roles with different responsibilities
- ask business questions only when code authoring depends on them, not by default in runtime UI
- treat `案件ID` as globally unique and never allow duplicates across the workflow
- default `onOpen` custom menu names to `便利ツール` unless the user explicitly requests another name

For role recipes and handoff prompts, read `references/team-playbook.md`.

For the document approval workflow under `書類/`, also read:

- `references/document-folder-map.md`
- `references/document-approval-rules.md`
