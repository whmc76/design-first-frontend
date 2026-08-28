# Imagegen Brief

Use image generation to resolve visual composition, atmosphere, hierarchy, material, density, and cross-surface continuity. Do not use it to invent behavior, replace the experience coverage matrix, or prove implementation feasibility.

## Before Prompting

Provide the image model only with decisions grounded in product truth:

- Coverage ID(s), artifact ID, route/view/mode, state, viewport, and the artifact's role in the approved set.
- The approved system frame or related artifact that governs shared shell, tokens, navigation, and product identity.
- Current route/screenshot and nearby product surfaces.
- Product design rules, brand temperature, and protected shell.
- Target viewport and real width/height budget.
- Dominant object, module order, and first-viewport outcome.
- Real labels, representative content lengths, counts, and media aspect ratios.
- Feasible controls and states from the action/data map.
- Spatial rules for rails, canvas, inspectors, and scroll ownership.

If key interaction or spatial behavior is unresolved, create a wireframe, annotated study, storyboard, or executable spike first.

## Prompt Shape

Include:

- Use case: `ui-mockup`.
- Asset type: high-fidelity frontend design artifact.
- Artifact ID, coverage IDs, and whether this is a system frame, dependent screen, state frame, overlay, or storyboard step.
- Product/page, target user, and primary job.
- Product archetype and dominant object.
- Existing app context and what must remain unchanged.
- Relationship to approved artifacts and the exact cross-frame elements that must remain continuous.
- Exact viewport and shell budget.
- Required modules in visual order with truthful labels/content.
- Width priority and visible panel relationships.
- State depicted and adjacent frames when the artifact plan assigns a state storyboard.
- Typography, material, color, media, icon, and density direction.
- Product-specific signature gesture.
- Explicit avoid list and impossible/fake capabilities to exclude.

## Prompt Template

```text
Use case: ui-mockup
Asset type: high-fidelity [desktop/mobile] frontend design artifact for [product/page]
Artifact and coverage: [A-ID] covers [C-IDs] as [system frame/dependent screen/state/overlay/storyboard step].
User and job: [user] must [primary outcome].
Current product context: [existing route/shell/design system]. Preserve [protected chrome/behavior].
Continuity source: follow [approved artifact/path] for [shell/navigation/tokens/type/icon/density]; change only [coverage-specific decisions].
State shown: [normal/loading/progressive/result/error/etc.].
Viewport and spatial contract: [dimensions], [fixed/elastic regions], [min/preferred behavior], [scroll/focus rule].
Dominant object: [object] receives [space/hierarchy]. Supporting/contextual regions: [...].
Required modules in order: [...].
Real content: [verbatim labels, representative prose/counts/media ratios].
Real controls only: [actions known to exist]. Show unavailable capabilities as [disabled/read-only/absent].
Visual direction: [composition], [typography], [material/layers], [palette], [density], [product-specific gesture].
Interaction cues visible in the static frame: [selection/focus/progress/disclosure].
Avoid: [generic card farm, fake controls, impossible data, cramped prose, oversized chrome, irrelevant gradients/glass, text overlap, tiny labels].
```

## Direction Review

Reject a generated direction when:

- It does not clearly satisfy its assigned coverage rows or contradicts another approved artifact that governs shared decisions.
- It changes protected shell/brand without authorization.
- It adds actions, data, counts, or capabilities absent from the feasibility map.
- Its dominant object is unclear or the first viewport is decorative.
- It relies on impossible text density, unreadable labels, or unrealistic empty content.
- Side rails, overlays, or fixed dimensions leave no viable space for the primary job.
- It hides required controls or uses visual controls that cannot be implemented accessibly.
- Its identity comes mainly from fashionable gradients, glass, glow, large radii, or generic cards.
- It only depicts a pristine default state when failure, progress, long content, or restoration defines the product.
- It compresses several complex screens into one contact sheet that is too small to govern text, spacing, geometry, or implementation.

## Artifact Iteration

- Use the experience coverage matrix to plan the artifact set before calling image generation. Do not let the first attractive frame silently become the entire product design.
- Compare a small number of genuinely different composition strategies for the system frame, not superficial color variants, when exploration is useful.
- Select based on experience intent and feasibility, not image beauty alone.
- Generate dependent artifacts in small coherent batches or one at a time, referencing the system frame and newest approved related frame when supported.
- Preserve stable artifact IDs and separate full-resolution files. A contact sheet is an index, not an authoritative implementation source.
- Review cross-frame continuity for shell geometry, navigation, tokens, typography roles, icons, density, content model, and task progression before approval.
- Annotate exact spatial, state, and interaction decisions that the bitmap leaves ambiguous.
- Once approved, record the source path and supersession rule in the design contract.
- If implementation discovery requires a material change, update or annotate the contract instead of silently drifting.

A single generated frame is sufficient only when `experience-coverage.md` permits the explicit single-surface exception.
