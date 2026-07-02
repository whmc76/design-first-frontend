# Browser Verification

Use this reference before final response.

## Required Checks

- Compile/type/lint/test checks relevant to touched files.
- Desktop screenshot at the target design width, commonly 1440-1600 wide.
- Mobile screenshot or viewport check around 390x844 unless the page is desktop-only.
- DOM checks for overflow and old structure removal.
- Interaction check for at least the primary tab/button/input changed by the redesign.
- Completed parity ledger: no FAIL, UNKNOWN, or unchecked rows before final.

## Useful DOM Metrics

```js
(() => {
  const rect = (selector) => {
    const el = document.querySelector(selector);
    if (!el) return null;
    const r = el.getBoundingClientRect();
    return { x: Math.round(r.x), y: Math.round(r.y), w: Math.round(r.width), h: Math.round(r.height) };
  };
  return {
    viewport: { w: window.innerWidth, h: window.innerHeight },
    overflow: document.documentElement.scrollWidth - document.documentElement.clientWidth,
    scrollHeight: document.documentElement.scrollHeight,
    keyModule: rect('[data-or-class-for-key-module]'),
    oldSelectorCount: document.querySelectorAll('[old-selector]').length,
    requiredIconCount: document.querySelectorAll('[required-icon-selector]').length,
    requiredControlCount: document.querySelectorAll('[required-control-selector]').length,
  };
})()
```

## Common False Positives

- Screenshot captured Suspense/loading state.
- Browser served stale build or wrong port.
- Route redirects to a different tab or default mode.
- HMR updated CSS but not component tree.
- `file://` preview failed to load module scripts.
- Mobile page is scrollable only inside an app shell; verify the actual scroll container.

## Visual Comparison Checklist

- Same macro layout as design: shell, columns, major module order.
- Same information architecture: no old grid/list/card remains where design replaced it.
- Same density: primary workflow visible in intended viewport.
- Same visual language: border/radius/surface/title/chip/button styles are shared.
- Same interaction state: selected tabs, previews, default mode, and empty/loading states make sense.
- No horizontal overflow, clipped right column, or unreachable mobile controls.
- Every parity ledger row has evidence. Do not close on "visually close" without a selector, screenshot, metric, interaction result, or API/database result.

## User-Complaint Simulation

Before final, write and answer five likely objections:

- "This module still has the old structure."
- "The design showed icons/checkboxes/previews but the implementation uses text/cards."
- "This button looks real but does nothing."
- "The first viewport still wastes space or hides the main workflow."
- "The page is using fake/mock data instead of generated or persisted data."

If any answer is weak, continue implementation or label the residual risk explicitly.
