# Imagegen Brief

Use this reference when composing the design-first imagegen prompt.

## Prompt Shape

Include:

- Use case: `ui-mockup`.
- Asset type: high-fidelity frontend page design mockup.
- Product and page name.
- Target user and page job.
- Existing app context: sidebar, header, route, workflow, current screenshot if available.
- Viewport: desktop dimensions and, when useful, mobile constraints.
- Required visible modules in exact order.
- Real labels, especially Chinese labels supplied by the user.
- Style direction based on domain:
  - Operator/SaaS: dense, restrained, work-focused, scannable.
  - Creative workspace: immersive preview plus tool/conversation controls.
  - Landing page: image-led first viewport, not dashboard cards.
- Palette and typography constraints.
- Interaction hints: tabs, segmented controls, previews, inspector, command bar.
- Explicit avoid list.

## Default Avoid List

- No marketing hero for an app workspace.
- No generic card mosaic.
- No decorative gradient orbs, bokeh blobs, or purple-blue gradient dominance.
- No hidden primary controls when the task is operational.
- No oversized header that pushes the real workflow below the first viewport.
- No fake browser chrome unless the user asks for a browser-frame mockup.
- No text overlap or tiny unreadable Chinese labels.

## Prompt Template

```text
Use case: ui-mockup
Asset type: high-fidelity desktop UI design mockup for [product/page]
Primary request: Redesign [page/module] for [target user] so they can [core job].
Existing context: [left nav/header/current page/nearby page to align with]. Use any attached screenshot for information architecture only unless told to preserve style.
Composition: [viewport], [grid/shell], [module order], first viewport must show [critical modules].
Required modules: [module 1], [module 2], [module 3].
Style: [operator console / creative workspace / SaaS / landing], [density], [radius], [border/shadow], [icon/asset use].
Palette: [base], [accent], status colors only for semantics.
Text: [verbatim labels].
Constraints: [must not include X], [must keep Y visible], [responsive note].
Avoid: [avoid list].
```

