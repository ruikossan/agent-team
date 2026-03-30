# Document Approval Rules

This file captures the current requested business flow for work under `書類/`.

## Worker-side create flow

When a worker exports or PDF-creates a case:

1. transfer the case into `現業課メニュー` target sheets
2. transfer the case into the `主務職シート`
3. link the `案件ID` cell to the manager-side spreadsheet for that case
4. write `未` to `課長`
5. write `未` to `主務職`
6. write `主務職待ち` to the overall status
7. ask which column in `各種書類シート` should receive the transfer if not already defined in code
8. write `未完` to the status cell immediately to the right of the chosen transfer column

## Manager-side approval flow

When staff approval is completed:

1. change `主務職` from `未` to `済`
2. change overall status from `主務職待ち` to `課長待ち`

When chief approval is completed:

1. change `課長` from `未` to `済`
2. change overall status from `課長待ち` to `確定済み`

## Completion flow

When the chief approval is done and the `主務職シート` overall status is `確定済み`:

1. change the corresponding `各種書類シート` status from `未完` to `完了`
2. transfer the `案件ID` into `2026年度 案件ID`

## Asking rules

Ask business questions only when code authoring depends on them.

Ask at code-design time for:

- what should be stored as `案件内容`
- which destination column in `各種書類シート` should receive the transfer when that mapping is not already encoded

Do not ask these in:

- worker dialogs
- sidebars
- runtime operator panels
- manager approval UI

## Case ID rule

`案件ID` duplication is not allowed.

Always treat `案件ID` as a globally unique key across:

- worker-side creation
- manager-side approval processing
- `現業課メニュー`
- `主務職シート`
- `各種書類シート`
- `2026年度 案件ID`

When implementing or updating code:

1. check for an existing `案件ID` before creating or inserting a new one
2. fail safely if a duplicate is detected
3. prefer explicit duplicate checks over assuming sequence generators are sufficient
4. preserve uniqueness even when retrying PDF creation or re-running transfer logic

## Menu naming rule

Unless the user explicitly requests another label, custom menus created in `onOpen` should use:

- `便利ツール`
