# Team Playbook

Use this file when the task is large enough that explicit role handoffs help.

## Role prompts

### Lead

Use when coordinating the whole task.

Prompt pattern:

`Own the task end-to-end. Decide scope, sequence the work, integrate results, and keep the critical path moving.`

### Explorer

Use when requirements or code paths are unclear.

Prompt pattern:

`Inspect the relevant area, answer the concrete question, and cite the files and lines that matter. Do not make edits unless explicitly asked.`

### Builder

Use when a bounded implementation slice is ready.

Prompt pattern:

`Implement the assigned change in the owned files only. You are not alone in the repo; do not revert unrelated edits. Report the files you changed and any verification you ran.`

### Reviewer

Use when the main risk is correctness or regression.

Prompt pattern:

`Review the change for bugs, regressions, missing tests, risky assumptions, and operational impact. Prioritize findings over summary.`

### Finisher

Use when the code is stable but adoption details still matter.

Prompt pattern:

`Tighten docs, examples, operator notes, naming, and release-readiness details without changing the intended behavior.`

## Suggested team compositions

### Small task

Keep everything in one agent unless there is a clear independent verification pass worth separating.

### Medium task

- Lead works locally
- Explorer or Builder may be delegated
- Reviewer may run as a final parallel pass

### Large task

- Lead stays on integration
- spawn multiple Builders only if file ownership is disjoint
- assign one Reviewer after implementation stabilizes
- add Finisher if docs or operator procedures changed

## Handoff checklist

Include these items in every delegation:

- exact goal
- file ownership or scope boundary
- constraints about unrelated edits
- required output format
- whether tests or checks are expected

## Completion checklist

The task is not complete until all apply:

- code and config changes are integrated
- verification status is known
- assumptions are called out
- remaining risk is explicitly stated if anything could not be checked
