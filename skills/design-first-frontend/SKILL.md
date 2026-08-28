---
name: design-first-frontend
description: Design and ship production frontend redesigns from an evidence-based visual, interaction, and multi-surface contract. Use for pages, multi-route products, workspaces, shells, or modules where cross-view continuity, spatial behavior, motion, real data/actions, implementation feasibility, and browser fidelity all matter. Also use when one mockup cannot cover the product, a screenshot implementation still feels like the old page, or a design looks good but does not work.
---

# Design-First Frontend

Turn a redesign request into a production experience, not a decorative mockup. The design contract includes layout, content behavior, interaction states, motion, data/actions, engineering constraints, and verification evidence. A beautiful image that cannot survive real content or be implemented faithfully is a failed design.

The goal is to reduce the user's design and QA burden. The user should not have to discover obvious layout, state, control, responsiveness, or implementation mismatches one at a time.

## Outcome Standard

A successful result must be all of the following:

- **Distinctive:** appropriate to the product and brand, with an intentional composition rather than a generic card grid.
- **Legible:** clear hierarchy, useful density, readable long content, and an obvious primary job in the first viewport.
- **Operable:** real actions work; loading, empty, long-content, error, terminal, disabled, focus, and selection states are coherent.
- **Spatially stable:** panels negotiate available space; important content does not become unusably narrow, overlap, or disappear during resize and state changes.
- **Performant and accessible:** motion, media, rendering, keyboard/focus, contrast, and reduced-motion behavior are proportionate to the product.
- **Buildable:** the visual contract maps to real components, handlers, data sources, assets, and an affordable implementation strategy.
- **Coverage-complete:** every scoped route, view, mode, critical state, and structural breakpoint is represented by approved design evidence or an explicit scope decision.
- **Verified:** the actual route is exercised in a real browser and compared against the contract with screenshots, DOM geometry, interactions, and runtime evidence.

## Non-Negotiables

- Inspect the scoped surface graph in a browser and inspect its owning code before proposing a redesign. One route or screenshot does not reveal sibling views, nested modes, state transitions, handlers, or shared-shell constraints.
- Create an experience coverage matrix and the required artifact set before broad implementation. Use the fewest artifacts that cover every distinct structural, interaction, state, and viewport decision—not one artifact by default and not every possible permutation.
- A single design frame is valid only for an explicitly single-surface scope with no important alternate route, mode, step, overlay, or state requiring a different visual decision.
- Do not use image generation as a substitute for interaction design or engineering. A bitmap cannot prove resizing, scrolling, focus, animation, data lifecycle, or task continuity.
- Freeze a **visual, interaction, and implementation contract** before broad implementation. If feasibility is uncertain, build a narrow spike first and then revise the artifact.
- Treat the newest approved artifact for each coverage row as authoritative. User instructions about preserved shell, navigation, brand, behavior, or scope override imagery.
- Preserve product truth. No invented business data, fake actions, decorative controls, or impossible capabilities. Every visible control maps to a real handler/route, a truthful disabled/read-only state, or removal.
- When information architecture changes, rewrite the owning component boundary. Do not preserve an obsolete DOM tree and attempt to disguise it with CSS.
- Do not let live content destroy the composition. Design and verify normal, minimum, maximum, empty, loading, error, and long-content cases. Summaries may clamp only when the full content remains accessible.
- For multi-panel workspaces, define ownership of width, scroll, focus, and collapse. Avoid independent fixed widths and absolute overlays competing for the same canvas.
- Motion must explain state, hierarchy, continuity, or causality. Specify trigger, duration class, property, interruption behavior, and reduced-motion fallback. Do not add ambient motion merely to appear premium.
- Do not claim completion from a mockup, component preview, typecheck, or build. Verify the real route and real representative data in a browser.
- Do not close while experience coverage contains unexplained, `PLANNED`, or `BLOCKED` rows, or while the parity ledger contains `TODO`, `FAIL`, `BLOCKED`, or unchecked items, unless the result is explicitly reported as incomplete.

## Choose the Right Design Evidence

Use one or more artifacts based on the risk:

- **Surface graph and coverage matrix:** routes, views, modes, nested flows, states, breakpoints, template families, and the artifact that governs each coverage unit.
- **Static visual artifact:** hierarchy, typography, material, density, and macro composition.
- **State storyboard:** loading, progressive work, populated, empty, error, failed, completed, collapsed, and alternate-tab behavior.
- **Annotated spatial study:** panel min/preferred/max widths, scroll owners, resize/collapse rules, overlays, and first-viewport budget.
- **Executable spike:** novel interactions, complex motion, virtualized or resizable panes, canvas behavior, or uncertain framework feasibility.

Do not spend time polishing a high-fidelity image while the key interaction or spatial model is unresolved.

## Workflow

### 1. Establish product truth

- Read repository instructions, design-system rules, tokens, and nearby product surfaces.
- Traverse every scoped route, view, mode, nested flow, and important return path. Capture representative normal, loading, empty, error, populated, terminal, overlay, and alternate-tab states.
- Identify the target user, page job, primary workflow, decision points, important content, and what must remain familiar.
- Inventory real data sources, handlers, routes, uploads/media, persistence, background lifecycles, and external dependencies.
- Read [references/experience-coverage.md](references/experience-coverage.md) and create the surface graph plus experience coverage matrix before choosing polished artifacts.
- State the observed problem and the first bad boundary: product model, shell, component tree, CSS cascade, data contract, interaction state, route, or rendered DOM.

### 2. Define experience strategy

- Choose the product archetype: creative workspace, operator console, editorial tool, dashboard, consumer flow, landing page, or another justified model.
- Write the hierarchy in plain language: what dominates, what supports, what stays peripheral, and what changes by task stage.
- Group scoped surfaces into shared shells and structurally distinct template families; state which decisions must remain continuous across them.
- Define spatial choreography: fixed vs. elastic regions, panel priority, min/preferred/max widths, collapse behavior, scroll ownership, and focus mode.
- Define interaction choreography: entry, selection, creation, progress, interruption, completion, failure, recovery, and return paths.
- Identify where motion materially improves orientation or causality.
- Read [references/experience-quality.md](references/experience-quality.md) and reject generic or structurally weak directions before generating polish.

### 3. Pass the feasibility gate

For every coverage unit, important visible module, and control, map:

- Real source of content and source of truth.
- Existing or required handler, navigation, persistence, and lifecycle ownership.
- Expected content extremes and media behavior.
- Framework/component reuse, rewrite boundary, and likely performance risk.
- Honest fallback if a dependency or capability is unavailable.

Build a narrow executable spike before freezing high fidelity when the design depends on uncertain resizing, drag/drop, canvas, animation, virtualization, media processing, streaming, or background-task behavior. Read [references/implementation-feasibility.md](references/implementation-feasibility.md).

### 4. Create and freeze the design contract

- Prefer supplied or approved design sources. If they do not cover the matrix and visual exploration is useful, use image generation and read [references/imagegen-brief.md](references/imagegen-brief.md).
- Plan stable artifact IDs and generate or select a coherent artifact set that covers the matrix. Preserve the approved system frame across dependent screens; do not ask an image model to invent product capabilities.
- Freeze the approved artifact set, coverage mapping, viewport(s), shell, module order, hierarchy, typography, materials, spatial rules, state storyboards, interaction details, motion rules, data/action contracts, and old structures to remove.
- Record explicit deviations from the artifact where browser behavior, real content, accessibility, or platform constraints require them.
- Read [references/design-contract.md](references/design-contract.md) and create the parity ledger from [references/parity-ledger.md](references/parity-ledger.md).

### 5. Map the contract to code

Locate each covered route/view and the first shared or local component/style/state boundary that owns its behavior. Map every contract item to:

- Existing owner and selector.
- Reuse, rewrite, remove, create, or rewire action.
- Data source and handler/lifecycle owner.
- State and content cases.
- Verification selector, geometry, screenshot region, interaction, or runtime evidence.

Include shared shell, route wrapper, old selectors, scroll containers, portals/overlays, focus management, and background lifecycles. Fix repeated layout smells at their shared abstraction rather than in each page.

### 6. Implement in truthful vertical slices

- Establish tokens and macro shell first: viewport budget, grid/flex constraints, `min-width: 0`, scroll ownership, layer strategy, and typography scale.
- Implement the primary workflow through one complete real state, then complete coverage units in dependency order: shared shell, template families, nested flows, critical states, and scoped breakpoints.
- Add remaining covered states and modules using real data/handlers. Preserve existing behavior unless the contract explicitly changes it.
- Keep visual and interaction state separate from business lifecycle state when collapsing, dismissing, switching tabs, or leaving the viewport must not cancel work.
- Use semantic structure and accessible native behavior before custom interaction abstractions.
- Make motion interruptible and state-driven. Prefer transform/opacity for frequent animation; avoid unnecessary layout thrashing and permanent `will-change`.
- Scope route-specific styles, remove obsolete competing selectors, and avoid specificity escalation as a repair strategy.
- Use established components and tokens where they strengthen coherence; do not force a generic design system component where it destroys the intended hierarchy.
- Update the ledger with evidence after each stable slice. Commit/checkpoint at meaningful, runnable stages when the repository workflow requires it.

### 7. Verify the real experience

- Run the narrowest relevant static checks, then exercise the real application boundary.
- Verify representative desktop widths specified by the product. Verify mobile only when mobile is in scope; never invent a mobile requirement for a desktop-only product.
- Exercise primary journeys, route/view transitions, nested modes, and state transitions—not just the initial render.
- Capture every required coverage unit and compare it module-by-module with its governing artifact ID. Use DOM geometry for spatial claims and screenshots for visual claims.
- Check long text, dense content, empty/loading/error states, media failure, focus/keyboard behavior, reduced motion, overflow, resize/collapse, and stale/old DOM removal.
- Inspect console/network/runtime errors and gather proportionate performance evidence for expensive media, motion, lists, or canvases.
- Read [references/verification.md](references/verification.md). Fix the largest structural or behavioral mismatch before color and micro-polish.

### 8. Run the quality challenge

Before completion, challenge the result from four angles:

- **User:** Can I understand the page, complete the primary job, recover from failure, and read real content without fighting the layout?
- **Designer:** Is the hierarchy intentional and distinctive, or is it a generic card farm with fashionable decoration?
- **Engineer:** Are component boundaries, state ownership, CSS, rendering cost, and fallback behavior sustainable?
- **Skeptic:** Which five visible or interactive issues would make the user say “it still looks the same,” “this is cramped,” or “this button is fake”?

Continue if any answer exposes a contract failure. Update the contract if a justified implementation discovery changes the design.

## Root-Cause Pattern for Redesign Failures

Before editing a reported mismatch, state:

- Observed symptom.
- First bad layer or boundary.
- Suspected root cause.
- Why it surfaced in this state or viewport.
- Whether the proposed change fixes the contract/owner or only patches the symptom.

Frequent root causes include an unexamined shared shell, fixed widths competing with an overlay, a wrong scroll owner, visual state coupled to task lifecycle, old selectors winning the cascade, fake mockup content, missing extreme-content states, a screenshot from the wrong route/build, and an artifact that was never feasible with the product's actual data or handlers.

## Completion Standard

The final report must include:

- Approved design source and any state/spatial/interaction artifacts.
- Experience coverage totals by route/view/template/state/viewport, artifact IDs, and zero unexplained, `PLANNED`, or `BLOCKED` rows.
- Root cause for redesign fixes.
- Structural, interaction, visual, motion, and engineering changes.
- Real routes/views and data states verified, target viewport(s), screenshots, DOM/interaction/runtime evidence, and relevant checks.
- Parity ledger totals with zero unreported `TODO`, `FAIL`, or `BLOCKED` rows.
- Explicit deviations from the artifact and why they improve truth, usability, accessibility, performance, or feasibility.
- Deployment/integration state when requested, plus residual risks and owner/next action for blockers.

Do not say “matches the design,” “production-ready,” or “complete” unless the rendered application and its important states satisfy the contract.
