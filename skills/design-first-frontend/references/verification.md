# Browser Verification

Verify the real experience, not merely the compiled component. Scale the checks to the risk, but never omit a required experience-coverage unit, primary journey, or scoped viewport behavior.

## 1. Runtime Preflight

- Confirm the exact checkout/branch/commit and server/container serving the page.
- Confirm route, product mode, authentication/session, data fixture or real representative record, and feature flags.
- Confirm the coverage ID, governing artifact ID, shared shell/template family, and expected entry/return path for each verification run.
- Reload or restart enough of the runtime to rule out stale HMR, cache, or bind-mount output.
- Capture console and network/runtime errors relevant to the flow.

## 2. Viewport and Spatial Checks

- Capture the authoritative design viewport.
- Check representative boundary widths immediately above and below layout transitions.
- Verify mobile only when it is in product scope.
- Record geometry for dominant and supporting regions, header/footer/sticky elements, scroll containers, and any overlay/portal.
- Confirm no unintended horizontal overflow, clipping, overlap, hidden primary action, or unusably narrow text/media.
- Expand/collapse/focus/resize panels and confirm the dominant object remains usable and the return path is clear.

Example geometry probe:

```js
(() => {
  const box = (selector) => {
    const element = document.querySelector(selector);
    if (!element) return null;
    const rect = element.getBoundingClientRect();
    return { x: Math.round(rect.x), y: Math.round(rect.y), w: Math.round(rect.width), h: Math.round(rect.height) };
  };
  return {
    viewport: { w: innerWidth, h: innerHeight },
    documentOverflowX: document.documentElement.scrollWidth - document.documentElement.clientWidth,
    primary: box('[data-primary-work]'),
    supporting: box('[data-supporting-panel]'),
    oldStructureCount: document.querySelectorAll('[data-old-structure]').length,
    modalCount: document.querySelectorAll('[aria-modal="true"]').length,
  };
})()
```

Use actual project selectors; placeholder selectors are not evidence.

## 3. State and Content Matrix

Exercise the relevant states with real or repository-approved representative data:

- Initial/first entry.
- Loading/generating and progressive/partial state.
- Typical populated state.
- Maximum/long text and dense content.
- Empty/no-results and media failure.
- Validation, dependency, network, or task failure.
- Success/completed, canceled, stale/restored, and alternate tabs/modes.

Confirm the hierarchy, actions, scroll, and content access remain coherent in each. Do not replace unavailable real states with invented business content.

Map every exercised state back to the experience coverage matrix. If a state reveals a structurally different surface or action hierarchy that was not planned, reopen the coverage and design gates instead of treating it as implementation polish.

## 4. Interaction and Lifecycle

- Exercise every changed primary control and representative secondary controls.
- Traverse representative navigation between covered routes/views/modes and verify selected navigation, shell continuity, task context, back/return behavior, and preserved work.
- Verify default, hover, pressed, selected, disabled, loading, and error behavior where applicable.
- Verify keyboard entry/order/activation, visible focus, focus containment only for real modals, and focus return after transient UI closes.
- Verify route/back/refresh/restoration behavior and persistence when the workflow requires it.
- For background work, explicitly test collapse/tab switch/unmount/restoration followed by completion, failure, and real cancel. Presentation changes must not swallow lifecycle events.
- Confirm fake, obsolete, and superseded controls/routes/selectors are absent.

## 5. Motion and Accessibility

- Observe important transitions at normal speed and during rapid reversal/repeated input.
- Confirm input is not blocked unnecessarily and the final state never depends on animation completion.
- Emulate `prefers-reduced-motion: reduce` and verify state changes remain understandable.
- Check semantic roles/names/states, contrast, status meaning beyond color, zoom/text scaling, and live announcements proportionate to the changed workflow.
- Use automated accessibility tooling when available, but verify the changed interaction manually as well.

## 6. Performance and Stability

Gather proportionate evidence when the redesign adds or changes heavy media, animation, large lists, global state, canvas, or dependencies:

- Repeated progress updates do not rerender or relayout the entire workspace unnecessarily.
- Resize/scroll/drag/animation remains responsive under representative content.
- Media uses appropriate thumbnail/full-resolution loading and does not create avoidable layout shift.
- New dependency or chunk cost is understood; secondary heavy UI can be deferred without harming the primary job.
- No maximum-update loops, leaked listeners, stale subscriptions, repeated requests, or console errors appear during the verified flow.

Use existing project budgets when available. Do not invent universal thresholds solely to manufacture a PASS.

## 7. Visual Comparison

For every artifact ID in the approved set, capture its mapped coverage units at the authoritative state and viewport. Compare implementation and artifact by region in this order:

1. Shell, dominant object, columns, and first-viewport allocation.
2. Module order, semantics, and state.
3. Typography, content density, and reading widths.
4. Surface, color, borders, depth, imagery, and icon treatment.
5. Interaction states and motion continuity.

Use image overlay/diff tooling when available, but interpret differences rather than optimizing a meaningless global pixel score. Dynamic content, browser font rendering, and documented feasibility/accessibility deviations may be legitimate.

Review the artifact set side by side for cross-surface continuity. A page can match its own frame and still fail if shell geometry, navigation, tokens, or task progression contradict sibling screens.

## 8. False Positives

- Screenshot captured Suspense/loading rather than the intended state.
- Wrong port, stale build, wrong route, redirect, default tab, feature flag, or user role.
- CSS HMR updated while component or server state did not.
- Browser zoom or OS scaling changed geometry.
- Component preview passed while the shared shell still overrides it.
- One polished route passed while sibling routes, nested modes, overlays, or structurally different states in the coverage matrix were never captured.
- Mock handlers made controls appear functional.
- Hidden old DOM still affects focus, accessibility, scroll, or lifecycle.

## 9. Final Challenge

Answer with evidence:

- Does the new surface still visibly inherit an obsolete shell, card rhythm, or layout constraint?
- Do real long content and dense states remain readable?
- Do all visible actions work or truthfully explain unavailability?
- Can the user understand progress, intervene, recover, and return without losing work?
- Does panel focus/collapse/resize preserve the primary canvas?
- Does motion clarify change without delaying work or harming reduced-motion users?
- Did the redesign introduce avoidable rendering, media, dependency, or maintenance cost?
- Does every scoped coverage row have approved design evidence and verified runtime evidence, with consistent shared decisions across the artifact set?

If an answer is weak, continue or report the exact blocker and incomplete state.
