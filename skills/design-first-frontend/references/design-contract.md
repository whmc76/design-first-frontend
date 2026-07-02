# Design Contract

Create this contract before implementation. Keep it short enough to remain useful during coding.

## Contract Fields

- **Design artifact**: path or URL.
- **Page shell**: route, viewport, sidebar/header behavior, grid columns.
- **Visual system**: background, surface, border, radius, shadow, spacing, typography, accents.
- **Module map**: every visible design module in order.
- **Parity ledger**: every visible module/control/icon/data action has a row with required evidence.
- **Interactions**: tabs, buttons, uploads, preview switching, drawers, default selected state.
- **Old structures to remove**: selectors/components/text that must disappear.
- **Behavior to preserve**: API calls, existing handlers, route compatibility, data state.
- **Verification selectors**: DOM selectors or visible text for each important module.

## Module Mapping Table

```markdown
| Design module | Existing owner | Action | Verification |
| --- | --- | --- | --- |
| Top compact status band | `OverviewPage.tsx`, `.overview-*` | rewrite | status band visible at y < 120 |
| Old hero banner | `.old-hero` | remove | selector count 0 |
```

After the mapping table, create the detailed parity ledger from `parity-ledger.md`. The mapping table identifies ownership; the parity ledger prevents missed visual details.

## Implementation Rules

- If a design module has no matching component, create or rewrite structure instead of trying to simulate it with CSS.
- If an old module remains visible, treat it as a failed implementation even when styling is improved.
- If a primary control is hidden below the first viewport in the design target, reduce header/module height before adding more content.
- If using generated design text, verify labels against product reality; remove fake capabilities or mock-only terms.
- Do not skip small controls. Platform marks, checkbox shapes, relation icons, selected states, upload affordances, preview slots, and helper labels need explicit ledger rows.
- For business pages, no generated plan, count, action button, or recommendation may be a mock-only visual. Add data-source rows for first-entry generation, persistence, readback, and manual refresh.
