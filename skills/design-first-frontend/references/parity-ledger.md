# Parity Ledger

The ledger prevents the user from becoming the implementation's manual diff tool. It covers appearance, behavior, product truth, and engineering evidence.

## Ledger Format

```markdown
| # | Coverage ID | Artifact ID | Type | Contract requirement | Current implementation | Required action | Evidence | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | C-01 | A-01 | spatial | work canvas keeps usable width while chat focuses | fixed columns squeeze canvas | rewrite shared grid constraints | geometry at target and boundary widths | TODO |
| 2 | C-02 | A-03 | lifecycle | collapsing monitor does not cancel live task | dismiss clears task id | split presentation/lifecycle state | collapse, finish, expand; terminal result visible | TODO |
```

Allowed statuses: `TODO`, `PASS`, `FAIL`, `BLOCKED`. Avoid “mostly,” “close,” or unproved PASS.

## Required Coverage

Add rows for every relevant category:

- **Experience coverage:** every scoped route/view/mode/template family, critical journey step, structurally different state, overlay, and viewport maps to its governing artifact and implementation evidence.
- **Structure:** route, shell, sidebar/topbar, module order, semantics, scroll owners, overlays/portals, old DOM removal.
- **Spatial:** region min/preferred/max behavior, first-viewport budget, resize transitions, collapse/focus, overflow, reading width.
- **Visual:** typography roles, layer/material model, color/status, borders/radii, icons/media, density, selected/focus/disabled styling.
- **Content/data:** real source, representative/extreme lengths, counts, empty/loading/error, persistence/readback, media failure.
- **Interaction:** every primary control, keyboard/focus, selection, uploads, tabs, disclosure, cancellation, recovery, alternate paths.
- **Lifecycle:** progressive/background state, restoration, terminal completion/failure, unmount/navigation cleanup.
- **Motion:** meaningful transitions, interruptibility, state consistency, reduced-motion outcome.
- **Performance/accessibility:** only risks materially introduced or affected by the redesign.
- **Removal/compatibility:** superseded selectors, routes, modals, fake controls, stale defaults, and preserved behavior.

## Evidence Rules

A row is PASS only with evidence appropriate to its claim:

- DOM selector/count for structure and removal.
- Bounding boxes/computed styles for geometry.
- Screenshot region or visual comparison for composition/material/typography.
- Real interaction result for actions and state changes.
- API/database/log/network evidence for data lifecycle when relevant.
- Keyboard/focus/accessibility-tree or semantic evidence for accessibility claims.
- Trace/profiler/bundle/network/runtime observation for material performance claims.
- Reduced-motion emulation or deterministic style/state evidence for motion fallback.

One piece of evidence may support several rows when it directly proves each claim. Do not add meaningless evidence just to increase counts.

## Automatic FAIL Conditions

Mark FAIL and continue when:

- A scoped coverage unit has no approved artifact/evidence, is represented only by an unreadable contact sheet, or silently inherits design decisions from an unrelated screen.
- Approved artifacts contradict each other on shared shell, navigation, tokens, hierarchy, or task continuity without a documented per-surface reason.
- Old structure remains and competes with or contaminates the new surface.
- A visible control is inert, fake, or wired to a mock-only success path.
- The static design is matched by breaking real data, lifecycle, focus, or accessibility.
- A multi-panel layout overlaps, starves the dominant region, or creates unreachable content at a scoped viewport.
- Long text/media/error/loading/restored states destroy hierarchy or usability.
- Visual state such as collapse/dismiss accidentally changes business lifecycle.
- The screenshot comes from a stale server, wrong route, wrong state, or component-only preview when the real route is available.
- Motion delays work, cannot be interrupted, causes large repeated layout cost, or ignores reduced motion.
- A shared fix is duplicated as page-specific patches and still fails on sibling surfaces in scope.

## Contract Deviations

If implementation intentionally differs from a bitmap:

1. Record the artifact expectation.
2. Record the real constraint or discovery.
3. Update the design contract.
4. Verify the improved behavior.

Mark PASS against the updated contract, not against an impossible screenshot. Undocumented visual drift remains FAIL.

## Final Summary

```text
Experience coverage: 9 rows — 9 approved, 9 implemented, 9 verified, 0 planned, 0 blocked.
Artifact set: 5 authoritative sources — system frame A-01, screens A-02/A-03, storyboard A-04, boundary frame A-05.
Parity ledger: 38 rows — 38 PASS, 0 FAIL, 0 BLOCKED.
Coverage: experience 6, structure 6, spatial 5, visual 7, content/data 4, interaction/lifecycle 7, motion/a11y/performance 3.
Key evidence: per-artifact screenshots, route/view transition replay, target and boundary geometry, no horizontal overflow, old overlay count 0, real action flow, collapse-to-terminal restoration, keyboard focus return, reduced-motion state.
```
