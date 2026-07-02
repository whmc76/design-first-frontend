# Design-First Frontend

Skill-only Codex plugin for imagegen-led frontend redesigns and faithful mockup-to-code implementation.

## What It Does

- Requires a design artifact before implementation unless explicitly skipped.
- Freezes a design contract before code changes.
- Creates a parity ledger for every visible module, control, icon, layout role, and data-backed action.
- Verifies visual fidelity with browser screenshots, DOM counts, selector checks, and user-complaint simulation.
- Blocks final completion while parity rows are failed, unknown, or unchecked.

## Install Locally

This project is registered in the personal Codex marketplace at:

```text
C:\Users\28687\.agents\plugins\marketplace.json
```

Install or refresh it with:

```powershell
codex plugin add design-first-frontend@personal
```

Start a new Codex thread after installation so the skill list is refreshed.

## Skill Path

```text
skills/design-first-frontend
```

## Validate

```powershell
python C:\Users\28687\.codex\skills\.system\plugin-creator\scripts\validate_plugin.py C:\Users\28687\plugins\design-first-frontend
python C:\Users\28687\.codex\skills\.system\skill-creator\scripts\quick_validate.py C:\Users\28687\plugins\design-first-frontend\skills\design-first-frontend
```
