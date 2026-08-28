# Experience Quality

Use this reference before choosing a visual direction and again during the final quality challenge. It is a decision framework, not a style catalog.

## Start With the Job and the Stage

Write one sentence for each:

- **Primary job:** what the user must be able to accomplish here.
- **Dominant object:** the work, decision, media, document, canvas, or status that deserves most space and contrast.
- **Supporting context:** information that improves the decision but should not compete with the dominant object.
- **Intervention point:** where the user can meaningfully change direction.
- **Stage change:** how the hierarchy changes before, during, and after the work.

If every module is equally prominent, the composition has no direction.

## Aesthetic Judgment

Evaluate the direction by these dimensions. Do not average away a serious failure.

### Composition and hierarchy

- The first viewport communicates one primary job and one dominant object.
- Space, scale, alignment, contrast, and cropping create hierarchy before borders and color do.
- Asymmetry is intentional and balanced; symmetry is used when comparison or calm is the job.
- Repetition establishes rhythm, but one or two controlled breaks create emphasis.
- Dense tools use grouping, baselines, and scan paths rather than many detached cards.

### Typography and content

- Display, section, body, metadata, numeric, and control text have distinct roles.
- Line length and line height support the actual language and content length.
- Long prose receives reading width and vertical rhythm; operational data receives compact alignment.
- Labels are specific and natural. Generated placeholder prose is not used to simulate sophistication.
- Truncation communicates that more content exists and provides a way to reveal it.

### Color, material, and depth

- Color carries hierarchy, identity, or status; it is not scattered decoration.
- Neutral surfaces belong to the product's brand temperature rather than a default cold SaaS palette.
- Borders, shadows, blur, grain, and translucency establish a coherent layer model.
- Status colors are reserved for semantics and remain distinguishable without color alone.
- Gradients, glass, glow, and oversized radii are rejected unless they reinforce the product concept.

### Identity and originality

- The page has a recognizable product-specific gesture: composition, editorial rhythm, control language, media treatment, or motion behavior.
- The gesture is carried through the shell, primary work, and result states rather than applied as isolated decoration.
- Direct imitation of a reference project's shell or signature interaction is avoided. Borrow principles, not product identity.

## Spatial Choreography

For every major region, record:

| Region | Priority | Min | Preferred | Max | Can collapse? | Scroll owner | Focus behavior |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Conversation | supporting/intervention | usable reading/input width | normal work width | focused width | yes | internal | expands when composing |
| Work canvas | dominant | preserves primary task | consumes remainder | flexible | no | page or internal | never covered by rails |
| Inspector | contextual | control-safe width | normal rail | bounded | yes | internal | opens for selected object |

Use product-appropriate values; the table defines relationships, not universal pixel constants.

### Rules

- Prefer one intentional page-level scroll owner. Nested scrolling is acceptable for persistent tools or media rails only when each boundary is visually and behaviorally clear.
- A rail may take space, overlay temporarily, or collapse; it must not unpredictably do all three.
- Set `min-width: 0` on flexible descendants that must shrink, and give critical regions a usable minimum rather than hoping content will wrap.
- Use `clamp()`, `minmax()`, intrinsic sizing, container queries, or explicit layout modes where they express the contract. Breakpoints are behavioral transitions, not a patch collection.
- Test widths immediately above and below layout transitions. Do not verify only the design-artifact width.
- When the user focuses a supporting panel, show how the dominant region yields space and how to return.
- Absolute/fixed positioning is for true overlays and transient layers, not for avoiding a shared layout decision.

## Interaction Quality

### Make the next meaningful action clear

- Primary and secondary actions have a visible priority and stable location.
- Defaults reduce unnecessary decisions without silently committing destructive or irreversible work.
- Frequent actions minimize pointer travel and repeated mode switching.
- Direct manipulation is preferred when the object and outcome are visible; commands/forms are preferred when precision or repeatability matters.
- Bulk and repeated workflows expose selection, progress, and recovery rather than forcing one-item-at-a-time work.

### Preserve continuity

- Switching tabs, collapsing a monitor, or resizing a panel does not accidentally reset business work.
- Selection and scroll position persist when doing so supports the task.
- Background progress remains visible without blocking unrelated work.
- Optimistic updates are used only when failure can be explained and reversed.
- Destructive actions communicate scope and recovery; do not hide risk behind visual polish.

### Disclose complexity progressively

- Keep essential context and controls visible.
- Place secondary detail near the object or decision it explains.
- Use drawers, inspectors, disclosure, and focus modes to add depth without compressing the primary canvas.
- Do not bury required operational controls in hover-only UI.

### Design the full state graph

Cover initial, loading/generating, partial/progressive, populated, empty, disabled, validation, success, failure, retry/recovery, canceled, and stale/restored states where applicable. Include keyboard focus, hover, pressed, selected, drag, and unavailable variants for changed controls.

## Motion and Performance

Motion should answer one of these questions:

- Where did this object come from or go?
- What changed because of my action?
- Which region now has focus?
- Is work progressing, blocked, complete, or failed?
- How are the previous and next states connected?

Specify each important motion as:

| Trigger | Purpose | Elements/properties | Timing class | Interrupt/cancel | Reduced motion |
| --- | --- | --- | --- | --- | --- |
| Open inspector | preserve spatial origin | rail transform + canvas resize | short transition | reverses from current state | instant state change |

Use the product's existing motion tokens when present. Otherwise keep feedback immediate, local transitions short, and major scene changes long enough to preserve continuity without delaying work. Prefer transform and opacity for frequent animation. Avoid animating large layout trees every frame, infinite ambient movement, scroll hijacking, or motion that blocks input.

## Efficiency Review

Evaluate the representative workflow, not the number of components:

- Time and actions from entry to the primary outcome.
- Repeated navigation, panel switching, scrolling, re-entry, or confirmation.
- Whether key status and context stay visible at decision points.
- Whether the layout adapts to task stage instead of reserving equal permanent space for every tool.
- Whether the interface allows correction at the smallest meaningful scope.
- Whether keyboard shortcuts, command access, filters, presets, or batch operations benefit frequent users without obscuring the base flow.

## Reject These “Premium” Shortcuts

- Generic floating card mosaics with no strong dominant region.
- Glass, blur, glow, gradients, huge radii, or thin gray text used as a substitute for hierarchy.
- Oversized headers and decorative whitespace that push the work below the first viewport.
- Tiny typography and narrow prose columns used to preserve a screenshot composition.
- Fixed sidebars and inspectors that starve the central work area.
- Showpiece animation that delays input, hides state, or has no reduced-motion path.
- Beautiful controls that are fake, hover-only, inaccessible, or disconnected from the product lifecycle.
- A screenshot-perfect default state that collapses under real content, errors, restoring, or task progress.
