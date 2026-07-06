# Design-First Frontend

Skill-only Codex plugin for imagegen-led frontend redesigns and faithful mockup-to-code implementation.

Author: Cyber Dick Lang ([whmc76](https://github.com/whmc76))

## What It Does

- Requires a design artifact before implementation unless explicitly skipped.
- Freezes a design contract before code changes.
- Creates a parity ledger for every visible module, control, icon, layout role, and data-backed action.
- Verifies visual fidelity with browser screenshots, DOM counts, selector checks, and user-complaint simulation.
- Blocks final completion while parity rows are failed, unknown, or unchecked.

## Install Locally

Install from GitHub with Codex:

```powershell
codex plugin add https://github.com/whmc76/design-first-frontend
```

For local development, clone this repository and install from the local plugin project:

```powershell
git clone https://github.com/whmc76/design-first-frontend.git
cd design-first-frontend
codex plugin add .
```

Start a new Codex thread after installation so the skill list is refreshed.

## Skill Path

```text
skills/design-first-frontend
```

## Validate

```powershell
python C:\Users\28687\.codex\skills\.system\plugin-creator\scripts\validate_plugin.py .
python C:\Users\28687\.codex\skills\.system\skill-creator\scripts\quick_validate.py .\skills\design-first-frontend
```

## License

MIT License. You may use, copy, modify, merge, publish, distribute, sublicense, and sell copies of this project, provided that the original copyright notice and permission notice are preserved.

Copyright (c) 2026 Cyber Dick Lang
