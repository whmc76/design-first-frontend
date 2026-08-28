# Design Contract

Create this contract before broad implementation. It should be precise enough to settle decisions during coding and compact enough to keep current.

## 1. Authority and Scope

- **Authoritative design source(s):** paths/URLs and which artifact governs visual, spatial, state, and interaction decisions.
- **Supersession:** newest approved artifact and any earlier artifact it replaces.
- **Route and viewport scope:** exact route/mode, desktop/mobile scope, target and boundary widths.
- **Protected product behavior:** real handlers, APIs, persistence, background lifecycles, navigation, and accessibility behavior that must remain.
- **Protected chrome:** shell/navigation/shared surfaces the user requires unchanged.
- **Explicit non-goals:** nearby surfaces, states, or platforms not included.

## 2. Experience Intent

- **Primary user and job.**
- **Dominant object and first-viewport outcome.**
- **Hierarchy:** dominant, supporting, contextual, and hidden-until-needed information.
- **Product-specific design gesture:** the composition, typography, material, control, media, or motion idea that creates identity.
- **Efficiency target:** repeated steps, mode changes, or space conflicts the design removes.

## 3. Artifact Set

List the evidence required for this problem:

- Static visual artifact and target viewport.
- State storyboard or state references.
- Annotated spatial study for multi-panel or resize-sensitive layouts.
- Executable spike for any interaction/technology uncertainty.

An image is not evidence for behavior it cannot depict.

## 4. Spatial Contract

```markdown
| Region | Role/priority | Min/preferred/max | Layout behavior | Scroll owner | Collapse/focus behavior | Boundary verification |
| --- | --- | --- | --- | --- | --- | --- |
| Work canvas | dominant | ... | consumes remaining width | page | never covered | geometry at target + boundary widths |
```

Also record:

- Page-level width/height budget, header/footer/sticky regions, and first-viewport visibility.
- Grid/flex/container-query behavior and layout transitions.
- Overlay/portal/layer rules and whether the background remains interactive.
- Reading-width and density rules for long prose, tables, media, and controls.

## 5. State and Interaction Contract

```markdown
| State/event | Visible hierarchy | Available actions | State owner | Persistence/return behavior | Evidence |
| --- | --- | --- | --- | --- | --- |
| background task collapsed | compact live status | expand, real cancel if supported | presentation separate from lifecycle | task continues and terminal state restores | browser interaction |
```

Cover the relevant initial, loading, progressive, populated, empty, long-content, disabled, success, failure, canceled, stale/restored, alternate-tab, and offline/dependency-failure states. Include keyboard/focus behavior for changed interactions.

## 6. Motion Contract

```markdown
| Trigger | Purpose | Elements/properties | Timing/token | Interrupt behavior | Reduced-motion result |
| --- | --- | --- | --- | --- | --- |
```

Do not include animation that has no explanatory purpose.

## 7. Data, Action, and Feasibility Contract

Use the feasibility map from `implementation-feasibility.md` for every visible business value and action. Record:

- Data source and source of truth.
- Handler/route/lifecycle owner.
- Loading, persistence/readback, refresh, failure, and fallback behavior.
- Content/media extremes.
- Required dependency or reusable component.
- Performance/accessibility risk and verification.

No primary row may remain unknown when the visual direction is frozen.

## 8. Visual System

- Typography roles, reading widths, numeric/metadata treatment, and real language/content constraints.
- Background/surface/layer model.
- Border, radius, shadow, blur, grain, and spacing logic.
- Brand and semantic color roles, including focus and status.
- Icon, illustration, thumbnail, aspect ratio, crop, and media-failure behavior.
- Existing tokens/components to reuse and justified route-specific additions.

## 9. Module-to-Code Map

```markdown
| Contract item | Existing owner/selector | Action | Data/handler owner | States | Verification |
| --- | --- | --- | --- | --- | --- |
| Elastic work shell | `WorkspaceShell`, `.workspace-*` | rewrite shared layout | presentation context | normal/focused/collapsed | DOM geometry at 1440/1920 |
| Old fixed overlay | `.old-overlay` | remove | n/a | all | selector count 0 |
```

Include shell, route wrapper, scroll owners, portals, focus management, old selectors, data fields, controls, and background lifecycles—not only visible cards.

## 10. Preserve, Remove, and Deviate

- **Must preserve:** behaviors, states, and product identity.
- **Must remove:** old components, selectors, routes, overlays, fake controls, and superseded defaults.
- **Known deviations:** difference from the visual artifact, reason, updated evidence, and approval status when material.

A deviation that improves truth, usability, accessibility, performance, or feasibility is valid when documented. Silent drift is not.

## Freeze Gate

Freeze only when:

- The primary workflow and important states are represented.
- Multi-panel spatial behavior is explicit.
- Important actions and content have real sources/owners.
- The largest technical uncertainty is inspected or spiked.
- The direction passes the experience-quality rejection checks.
- Verification evidence can be gathered for every parity row.
