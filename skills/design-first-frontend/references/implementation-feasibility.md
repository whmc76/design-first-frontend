# Implementation Feasibility

Use this reference before freezing a high-fidelity direction and when mapping the contract to code. Its purpose is to prevent attractive but fictional UI.

## Feasibility Map

Create one row per experience coverage unit and important module, action, and state:

```markdown
| Coverage/artifact | Requirement | Real data/source | Handler/lifecycle | Existing owner | Build strategy | Main risk | Fallback | Verification |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| C-02 / A-03 | Collapse live monitor | task snapshot + local presentation state | collapse must not release task | shared provider | split lifecycle and presentation state | terminal event lost while collapsed | persistent compact status | collapse, complete task, restore terminal UI |
```

Do not approve a direction while a primary capability has an unknown source, owner, handler, or fallback.

## When to Build a Spike

Build the smallest executable proof when the experience depends on behavior that cannot be validated in a bitmap or confidently inferred from the existing stack:

- Resizable, dockable, or multi-scroll workspaces.
- High-frequency canvas, timeline, drag/drop, zoom, or pointer interactions.
- Virtualized long lists or large media grids.
- Streaming, background-task restoration, progressive generation, or cancellation.
- Complex shared-layout transitions or choreography across portals.
- Browser media APIs, image/video processing, font metrics, or platform-specific behavior.
- A new UI dependency whose bundle, styling, accessibility, or lifecycle behavior is uncertain.

The spike should prove the riskiest invariant with representative content. It is disposable unless its boundaries and quality are suitable for production.

## Architecture Decisions

### Ownership

- Identify the route owner, shell owner, business source of truth, presentation owner, and lifecycle owner.
- Map shared owners and route-local owners across the experience coverage matrix so sibling surfaces do not reimplement the same shell, state, or navigation contract.
- Keep ephemeral visual state separate from persistent or background business state.
- Fix common sizing, overlay, scroll, and state problems at the shared owner when multiple surfaces reproduce them.
- Avoid moving feature state into a generic global context merely to make a layout convenient.

### DOM and semantics

- Change structure when semantics change. Tables, lists, timelines, documents, canvases, dialogs, inspectors, and navigation should keep appropriate roles and interaction models.
- Prefer native controls and semantic elements; enhance rather than replace their focus, keyboard, form, and accessibility behavior.
- Portals and overlays must have explicit layer, focus, dismissal, background interaction, and viewport rules.

### CSS and layout

- Establish tokens and shared primitives for the redesigned scope before accumulating one-off values.
- Define the containing block and scroll owner of every positioned or sticky element.
- Use grid/flex constraints that reflect spatial priority. Verify `min-width`, intrinsic content, wrapping, and overflow at each nested boundary.
- Remove obsolete selectors and layout overrides. Do not solve ownership mistakes with `!important`, arbitrary z-index escalation, or duplicate media-query patches.
- Prefer container-aware module behavior when modules can live in more than one shell.

### Data and actions

- Bind visible values to real sources. If data is unavailable, show an honest empty/generating/error state.
- Model first-entry, persistence/readback, refresh/regenerate, stale cache, and partial data when applicable.
- Every action must have a handler, navigation target, form behavior, or explicit disabled/read-only explanation.
- Do not use `console.log`, no-op callbacks, delayed mock promises, or local-only fake success to simulate completeness.
- Preserve cancellation, completion, failure, restoration, and cleanup semantics across unmount and navigation.

### Content and media

- Use representative minimum, typical, and extreme content lengths during implementation.
- Reserve media aspect ratio/space to prevent layout shift; define object fit, focal behavior, failure, loading, and preview/full-resolution behavior.
- Avoid loading full-resolution media for every thumbnail or eagerly mounting expensive offscreen content.
- Fonts, icons, and imagery must have a licensing/source path appropriate to the repository.

### Performance

- Follow existing budgets and tooling when present. When the change introduces meaningful cost, record a proportionate before/after observation for bundle, render/update, interaction responsiveness, layout shift, memory, or network/media behavior.
- Avoid global subscriptions and unstable context values that rerender the whole workspace on frequent progress updates.
- Virtualize only when content size justifies its complexity; paginate, reveal, or window consistently with the product workflow.
- Lazy-load secondary heavy modules when it does not delay the primary job or create disorienting layout changes.
- Use animation libraries only when their coordination benefit outweighs dependency and runtime cost.

### Accessibility

- Define keyboard order, visible focus, labels/names, selected/expanded/disabled semantics, error association, live status announcements, and focus return for changed workflows.
- Preserve background access for non-modal workspaces; use modal semantics only for genuinely blocking interaction.
- Verify zoom/text scaling and contrast in the actual theme. Do not encode status by color alone.
- Provide reduced-motion behavior that preserves state clarity.

## Implementation Sequence

Prefer a runnable vertical slice:

1. Shared shell and spatial constraints.
2. Primary object and one real end-to-end action/state.
3. Background lifecycle, restoration, failure, and cleanup.
4. Secondary modules and alternate states.
5. Motion and polish after structure, content, and actions are stable.
6. Browser verification and removal of superseded DOM/CSS/routes.

This order is guidance, not permission to ignore repository-specific workflow.

## Feasibility Gate

Before broad implementation, verify:

- Every approved coverage unit and artifact has a feasible owner/build strategy, or is explicitly blocked before design freeze.
- Primary workflow has real data and handlers.
- Important states have owners and truthful UI.
- Spatial rules are expressible in the current shell without overlap or unusable content widths.
- Motion has a state model and reduced-motion path.
- New dependencies are necessary and compatible.
- Extreme content/media has a strategy.
- Accessibility and performance risks have a verification plan.
- The largest uncertainty has been resolved by inspection or a spike.

If a primary row fails, revise the design rather than hiding the gap in implementation.
