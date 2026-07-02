# Parity Ledger

Use this file to prevent the user from doing module-by-module QA manually.

## Before Coding

Create a ledger from the design artifact and current page.

```markdown
| # | Design requirement | Current implementation | Required action | Evidence selector/check | Status |
| --- | --- | --- | --- | --- | --- |
| 1 | Platform choices use brand mark + square checkbox | text-only tile | rewrite JSX and CSS | `.creator-platform-mark` count = 8; `.creator-platform-checkbox` count = 8 | TODO |
| 2 | Non-music asset type is one preview/replace slot | middle file list remains | remove middle list from DOM | `.creator-assets-layout.single-slot`; `.creator-asset-focus .creator-asset-row` count = 0 | TODO |
```

## Required Columns

- **Design requirement**: concrete visible requirement, not "make nicer".
- **Current implementation**: what exists now and why it mismatches.
- **Required action**: reuse, rewrite, remove, create, rewire data, or preserve.
- **Evidence selector/check**: DOM selector, text check, count, style metric, screenshot region, API check, or interaction.
- **Status**: TODO, PASS, FAIL, BLOCKED. Avoid "mostly".

## What Must Get A Row

- Shell/sidebar/topbar/page chrome when visible in the artifact.
- Every major module in visual order.
- Every important control shape: checkbox, segmented control, icon button, upload button, tab, status chip, filter, preview, table row.
- Every required icon/media mark: brand icons, relationship icons, thumbnails, avatars, uploaded asset previews.
- Every layout semantic: table, timeline, card grid, right rail, split pane, single-slot preview, multi-item list.
- Every data-backed value or action: generated plan, refresh button, save action, upload, delete, selected state, first-entry missing-data behavior.
- Every old module that must disappear.

## PASS Rules

A row is PASS only when there is evidence:

- DOM selector/count confirms the structure.
- Screenshot confirms visible placement and density.
- Style metric confirms size/position when relevant.
- Interaction test confirms the control works or is correctly disabled.
- API/database check confirms generated/persisted business data where applicable.

## FAIL Rules

Mark FAIL and keep working when:

- The old DOM still exists but is hidden behind CSS.
- The design uses an icon/control shape and the implementation uses plain text.
- A single-slot design is implemented as a file list.
- A table/timeline/right rail is replaced with generic cards.
- A button has no real action, route, disabled state, or read-only explanation.
- Live data stretches the page so the first viewport no longer matches the design.
- The screenshot is from a loading state, stale server, or wrong route.

## Final Summary Format

```text
Parity ledger: 18 rows, 18 PASS, 0 FAIL, 0 UNKNOWN.
Key evidence: platform mark count 8, checkbox count 8, old asset list count 0, no horizontal overflow, screenshot saved at ...
```

