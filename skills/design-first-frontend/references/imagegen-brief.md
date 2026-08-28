# Imagegen Brief

Use image generation to resolve visual composition, atmosphere, hierarchy, material, and density. Do not use it to invent behavior or prove implementation feasibility.

## Before Prompting

Provide the image model only with decisions grounded in product truth:

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
- Product/page, target user, and primary job.
- Product archetype and dominant object.
- Existing app context and what must remain unchanged.
- Exact viewport and shell budget.
- Required modules in visual order with truthful labels/content.
- Width priority and visible panel relationships.
- State depicted and, when useful, adjacent frames for a small state storyboard.
- Typography, material, color, media, icon, and density direction.
- Product-specific signature gesture.
- Explicit avoid list and impossible/fake capabilities to exclude.

## Prompt Template

```text
Use case: ui-mockup
Asset type: high-fidelity [desktop/mobile] frontend design artifact for [product/page]
User and job: [user] must [primary outcome].
Current product context: [existing route/shell/design system]. Preserve [protected chrome/behavior].
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

- It changes protected shell/brand without authorization.
- It adds actions, data, counts, or capabilities absent from the feasibility map.
- Its dominant object is unclear or the first viewport is decorative.
- It relies on impossible text density, unreadable labels, or unrealistic empty content.
- Side rails, overlays, or fixed dimensions leave no viable space for the primary job.
- It hides required controls or uses visual controls that cannot be implemented accessibly.
- Its identity comes mainly from fashionable gradients, glass, glow, large radii, or generic cards.
- It only depicts a pristine default state when failure, progress, long content, or restoration defines the product.

## Artifact Iteration

- Compare a small number of genuinely different composition strategies, not superficial color variants, when exploration is useful.
- Select based on experience intent and feasibility, not image beauty alone.
- Annotate exact spatial, state, and interaction decisions that the bitmap leaves ambiguous.
- Once approved, record the source path and supersession rule in the design contract.
- If implementation discovery requires a material change, update or annotate the contract instead of silently drifting.
