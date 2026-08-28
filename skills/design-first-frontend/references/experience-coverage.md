# Experience Coverage

Use this reference before selecting or generating design artifacts when the redesign spans more than one route, view, mode, step, overlay, breakpoint, or structurally distinct state. The goal is coverage without generating every possible permutation.

## 1. Build the Surface Graph

Traverse the scoped product and record the surfaces a user can actually reach:

- Shared shells, navigation levels, and role/product modes.
- Routes and route parameters that materially change the experience.
- Tabs, inspectors, drawers, dialogs, popovers, canvases, editors, detail views, and focus modes.
- Multi-step creation, review, approval, recovery, and return paths.
- Loading, empty, populated, long-content, error, disabled, progressive, terminal, stale/restored, and dependency-failure states.
- Scoped viewport or container transitions that change composition or control access.

Do not treat a URL as the only unit. Several routes may share one visual template, while one route may contain several structurally different modes.

Create the experience coverage matrix:

```markdown
| Coverage ID | Journey/entry | Route + mode | Surface/template family | State/event | Viewport/container | Distinct design decision | Artifact ID | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| C-01 | open project | `/projects/:id` overview | project workspace shell | populated | 1440 desktop | baseline shell and navigation hierarchy | A-01 | APPROVED |
| C-02 | edit asset | `/projects/:id` editor | editor workspace | inspector open | 1440 desktop | canvas/inspector width and focus ownership | A-02 | PLANNED |
| C-03 | failed publish | publish dialog | blocking recovery flow | error | 1440 desktop | recovery actions and preserved work | A-03 | PLANNED |
```

Allowed planning statuses: `PLANNED`, `APPROVED`, `OUT_OF_SCOPE`, `BLOCKED`. Do not use `OUT_OF_SCOPE` merely to avoid designing a reachable part of the requested workflow.

## 2. Collapse the Graph into Coverage Units

Avoid combinatorial explosion by grouping surfaces that share the same meaningful design decisions. A separate visual artifact is required when a row changes one or more of:

- Shared shell, navigation level, dominant object, or macro region structure.
- Primary job, action hierarchy, or task stage.
- Interaction model, such as browse vs. edit, canvas vs. table, or inline vs. blocking flow.
- Layer model, including a material drawer, inspector, modal, comparison view, or focus mode.
- Content model or density enough to change hierarchy, scrolling, reading width, or media treatment.
- Failure, progress, completion, or restoration behavior that materially changes layout or available actions.
- Scoped breakpoint/container behavior that reorganizes or removes important regions.

Use annotations or state notes instead of another high-fidelity frame when only copy, values, a small validation message, or a control's ordinary hover/pressed treatment changes.

Document why grouped rows can safely share an artifact. If that rationale is uncertain, keep them separate until the design proves they can converge.

## 3. Plan the Artifact Set

Assign stable artifact IDs before generating polished visuals:

```markdown
| Artifact ID | Coverage IDs | Artifact type | Purpose | Required source/reference | Output path | Approval |
| --- | --- | --- | --- | --- | --- | --- |
| A-01 | C-01, C-04 | system frame | establish shared shell, tokens, and navigation | current product + brand rules | `design/a-01-system.png` | pending |
| A-02 | C-02 | screen frame | resolve editor composition and inspector behavior | A-01 | `design/a-02-editor.png` | pending |
| A-03 | C-03 | state storyboard | show publish failure and recovery continuity | A-01, A-02 | `design/a-03-publish-recovery/` | pending |
```

For multi-surface work, the set normally includes only the evidence the matrix proves necessary:

- A system frame for shared shell, navigation, typography, material, density, and core tokens.
- One frame for each structurally distinct screen/template family.
- A storyboard or executable spike for important multi-step or stateful transitions.
- Separate overlay/focus-mode evidence when it changes hierarchy, space, or recovery.
- Boundary viewport artifacts when responsive behavior changes structure rather than merely scaling it.

A single design frame is acceptable only when the scoped matrix contains one structural coverage unit and no important alternate route, mode, step, overlay, or state needs a different visual decision. Record that exception explicitly.

## 4. Generate a Coherent Artifact Set

- Establish and approve the system frame before generating dependent screens when no authoritative design system already exists.
- Generate dependent artifacts in small coherent batches or one frame at a time, reusing the system frame and the newest approved related frame as visual references when the tool supports reference editing.
- Review cross-frame continuity and keep protected shell, navigation geometry, typography roles, tokens, icons, density, and product identity stable across the set unless a coverage row explicitly changes them.
- Put the artifact ID, coverage IDs, route/mode, state, viewport, and relationship to the system frame in every prompt.
- Use real labels, representative content, controls, and product capabilities for that coverage unit.
- Save separate full-resolution artifacts as the authoritative sources. A contact sheet may be used as an index or review overview, but never as the only source for text, spacing, geometry, or implementation.
- When continuity drifts, repair or regenerate the owning frame before approval. Do not normalize conflicting artifacts during implementation by guessing.

Image generation is optional. Supplied designs, Figma frames, annotated browser captures, wireframes, and executable spikes can satisfy rows when they carry the needed evidence.

## 5. Coverage Gate

Do not freeze the design contract or begin broad implementation until:

- Every scoped surface-graph node is represented by a coverage row.
- Every row is mapped to an approved artifact, deliberately `OUT_OF_SCOPE`, or explicitly `BLOCKED`.
- Every primary journey has entry, task, success/terminal, failure/recovery, and return-path evidence proportionate to its design risk.
- Shared shell and visual-system decisions are consistent across dependent artifacts.
- Critical navigation, overlays, focus modes, and nested workflows have both visual and interaction evidence.
- Each artifact maps to real data/actions, an implementation owner, and planned browser verification.
- There are no unexplained gaps, duplicate contradictory frames, or artifacts with unknown scope.

`BLOCKED` rows make the result incomplete. Do not silently reduce the requested scope or present one attractive frame as the design for an uncovered product.
