---
name: design-first-frontend
description: Design-first frontend workflow for Codex imagegen-led page redesigns and faithful implementation. Use when the user asks to redesign, restyle, rebuild, or implement a frontend page/module from a generated design mockup, especially when they mention imagegen, design draft, matching the design, style consistency, module restyling, visual fidelity, screenshot verification, or complaints that the implementation still looks like the old page.
---

# Design-First Frontend

Use this skill to turn a frontend redesign request into a controlled design-to-code workflow. The default standard is: generate or select a design image first, freeze the implementation contract, map every visible module to code, then verify with screenshots and DOM metrics before claiming completion.

The point is to reduce the user's manual QA. If the user has to point out obvious module-level mismatches one by one, the workflow has failed even if the final page eventually improves.

## Non-Negotiables

- Do not start code implementation for a visual redesign until a design artifact exists, unless the user explicitly asks to skip imagegen.
- Treat the design image as an implementation contract, not inspiration.
- When the user supplies a design screenshot or mockup after an earlier generated design, the user-supplied artifact supersedes the generated one unless they explicitly say otherwise. Re-freeze the contract from the newest user artifact before editing.
- Do not preserve old JSX/HTML structure when the design changes information architecture. Rewrite the module boundary that owns the old layout.
- If the design artifact shows a different app shell, sidebar, topbar, or page chrome, that shell is part of the contract. Do not keep the old shell just because it is shared or convenient; create a scoped replacement for the redesigned route when changing the shared shell would be too broad.
- If the user explicitly says an existing shell, sidebar, topbar, navigation, route wrapper, or shared chrome must stay unchanged, that instruction overrides the screenshot shell. Freeze the redesign contract around the page content area only, and verify the preserved shell was not modified.
- Match the generated or supplied screenshot at the macro-layout level before tuning colors: sidebar width/order, topbar height/actions, first-viewport module positions, column widths, card heights, and visible text density must all be checked against the artifact.
- Preserve design semantics. A table in the artifact must be implemented as a table-like structure, a timeline as a timeline, a right rail as a right rail, and top filters as top filters; replacing these with generic cards is a mismatch even if the labels are present.
- Do not let live data destroy the design density. Clamp or summarize long records in cards, matrices, tables, and timelines so the rendered page keeps the same rhythm as the design while preserving access to the underlying data elsewhere.
- Do not use mock records, invented controls, or placeholder domain data to make a business page appear complete. If the real page has no persisted data on first entry, implement the data lifecycle: explicit generating/loading state, generation from real inputs, persistence to the owning table/API, subsequent reads from that table/API, and a manual refresh action that regenerates and updates the stored record.
- Do not call the work complete from typecheck/build alone. Capture real browser screenshots and inspect for visual drift, overflow, and old-module residue.
- Before coding, create a parity ledger for every visible module and control in the design: layout role, visual control shape, icon/media requirement, data source, implementation owner, and DOM verification selector. Do not rely on memory of the mockup.
- A design element that appears in the mockup but is missing from the parity ledger is a missed requirement. This includes small controls such as checkboxes, platform icons, relation icons, upload affordances, selected states, empty states, and helper labels.
- A parity item can only be marked PASS with evidence: DOM selector/count, screenshot region, rendered text, style metric, or interaction result. "Looks close" is not evidence.
- Do not final while any parity ledger row is FAIL, UNKNOWN, or NOT CHECKED unless you explicitly label the work incomplete and explain the blocker.
- If the user says "it still looks the same", assume the wrong layer was changed. Find the first bad boundary: design structure, component tree, style cascade, data contract, route, or rendered DOM.

## Workflow

1. **Frame the brief**
   - Identify product type, target user, page job, key workflows, and what must stay from the existing UI.
   - Classify the surface: operator console, SaaS dashboard, creative workspace, landing page, mobile tool, game, etc.
   - Read existing design rules and nearby pages before generating a design.

2. **Generate or select the design**
   - If no suitable design exists, use imagegen to produce a high-fidelity UI mockup.
   - Include exact viewport, app context, visible modules, density, palette, typography, real labels, and constraints.
   - Read `references/imagegen-brief.md` when composing the prompt.
   - Save or cite the generated image path in the work log/final response.

3. **Freeze a design contract**
   - Before editing code, write a short implementation contract in the working notes or update:
     - Page shell and grid, including whether the old global shell/sidebar/topbar must be replaced for this route.
     - Module list in visual order.
     - Fixed dimensions and density targets: sidebar width, topbar height, first-row height, card heights, primary column widths, and which modules must be visible in the first viewport.
   - Key states and interactions.
   - Data lifecycle: persisted source of truth, first-entry behavior when records are missing, loading/generating/error states, manual refresh/update behavior, and which UI areas must remain empty instead of showing mock content.
   - Visual tokens: background, border, radius, spacing, accent colors.
   - Must-remove old modules and must-preserve existing behavior.
   - Protected chrome: list any existing sidebar/topbar/shared navigation the user said not to change.
   - Supersession rule: name which artifact is authoritative when more than one screenshot or mockup exists.
   - Read `references/design-contract.md` for the checklist.
   - Read `references/parity-ledger.md` and create the ledger before editing.

4. **Map design to code**
   - Locate the owning route/component and the style source that actually renders the page.
   - Create a module-to-code mapping table:
     - Design module.
     - Existing component/CSS selector.
     - Action: reuse, rewrite, remove, or create.
     - Verification selector or visible text.
   - If the design changes layout semantics, change JSX/HTML first; CSS-only work is insufficient.
   - Include shell-level rows in the mapping table: old sidebar, old topbar, page wrapper, route owner, and shared layout classes. A redesign that leaves the old shell visible has failed unless the contract explicitly preserves it.
   - Include data-source rows in the mapping table for every visible business field: API/table/source, first-entry missing-data behavior, generation trigger, refresh trigger, and fallback text. A visible mock value without a source is a failed mapping.
   - Include semantics in the mapping table: table vs. card grid, right rail vs. inline section, top filters vs. profile strip, fixed-width sidebar vs. inherited nav.
   - Include control-shape rows for visual controls: checkbox vs. pill, icon+text vs. text-only, brand/platform mark vs. generic initial, single-slot preview vs. file list, disabled state vs. hidden action.

5. **Implement by module**
   - Replace old structure at the shared owner, not only the nearest visible call site.
   - Keep styles scoped to the page or established design-system classes.
   - Reuse existing data and handlers where behavior is unchanged.
   - Wire every visible business control to a real action, navigation, disabled/loading state, or explicit read-only treatment. Do not leave generated-plan, refresh, evidence-update, filter, or view-more controls as inert visual elements.
   - Remove or neutralize old CSS selectors that still force old cards, grids, banners, hidden rails, or oversized sections.
   - Keep one visual system across modules: same border weight, radius, title density, field density, chips, buttons, and status colors.
   - Work through the parity ledger, not through vague page areas. After each major module, update PASS/FAIL status with the selector or screenshot evidence that proves it matches the contract.

6. **Verify in browser**
   - Run the narrowest compile/test checks for touched files.
   - Start or reuse a local server, then capture desktop and mobile screenshots. If a server cannot run, state why and use the best available fallback.
   - Use DOM metrics, not just eyeballing, for:
     - `scrollWidth === clientWidth` or no unintended horizontal overflow.
     - Key modules visible in intended viewport.
     - Old selector count is zero for removed structures.
     - Primary buttons/tabs/inputs are accessible and clickable.
     - Macro contract counts match: number of top filters, stage columns, matrix rows, action items, and bottom cards.
     - Protected shell selectors and dimensions are unchanged when the user asked to keep existing navigation/chrome.
     - Missing-data, generated-data, persisted-data, and manual-refresh states use real API/table behavior rather than mock content.
     - Each parity ledger row has a PASS/FAIL status and evidence.
   - Read `references/verification.md` for concrete checks.

7. **Iterate against the design**
   - Compare screenshot to design module-by-module.
   - Fix largest structural mismatch first, then density, then polish.
   - If implementation must deviate from the design, state the reason and update the design contract.
   - When a screenshot comparison shows the old navigation, old page chrome, old card rhythm, or unclamped live data, return to component-tree/layout changes. Do not treat those as CSS polish.
   - If the rendered page still visually resembles the old implementation more than the artifact, mark the verification as failed and continue from the owning component or shell.
   - Run a final "user-complaint simulation": list the top 5 things the user would likely call out as "not like the design" and verify each against the screenshot/DOM before final.

## Root-Cause Pattern For Redesign Bugs

When the user reports visual mismatch, state these before editing:

- Observed symptom.
- First bad layer or boundary where behavior becomes wrong.
- Suspected root cause.
- Why it surfaced now.
- Whether the change is a root-cause fix or a symptom patch.

Common first bad layers:

- Design contract missing: no frozen module list, so implementation drifted.
- Component tree wrong: old card/grid/rail still renders.
- CSS cascade wrong: new styles added but old selectors win.
- Data/route wrong: code changed a different page, state, tab, or mode.
- Verification wrong: screenshot captured loading state, stale build, wrong viewport, or old dev server.
- Optional integration wrong: optional service or executor auto-runs and steals the default flow.
- Parity ledger missing: small but important design controls were never listed, so the user had to identify them manually.
- Data contract missing: the mockup invented values/actions and implementation shipped them as fake business UI.

## Completion Standard

Final response must include:

- Design artifact path or design source.
- Root cause if this was a mismatch/fix request.
- What changed structurally and visually.
- Verification run, including screenshot/browser checks.
- Parity ledger summary: total rows, PASS rows, any unresolved FAIL/UNKNOWN rows.
- Residual risk, especially blocked visual checks or known unrelated build failures.

Do not say "matches the design" unless a real rendered screenshot was compared against the design contract.
