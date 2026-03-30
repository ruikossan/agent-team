# Document Folder Map

Current relevant files under `書類/`:

- `書類/現業課メニュー/現業課メニュー.xlsx`
- `書類/案件ID/2026年度  案件ID.xlsx`
- `書類/内航受入/worker/code.txt`
- `書類/内航受入/worker/SIdebar.html`
- `書類/内航受入/manager/code.txt`
- `書類/内航受入/manager/Sidebar.html`
- `書類/内航受入/manager/StampSidebar.html`
- `書類/2油種/worker/code.txt`
- `書類/2油種/worker/index.html`
- `書類/2油種/manager/code.txt`
- `書類/2油種/manager/index.html`

Recommended inspection order for future work:

1. target `worker/code.txt`
2. target `manager/code.txt`
3. target HTML sidebar or dialog files
4. shared destination workbooks in `現業課メニュー` and `案件ID`

## Known pattern

Existing code already suggests these recurring mechanisms:

- PDF export from spreadsheet
- case ID generation and recording
- draft and final PDF folders
- queue or approval tracking
- status syncing to external sheets

Reuse those patterns where possible before inventing a new data path.
