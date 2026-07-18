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

Apache License 2.0. Redistribution must preserve the license text and the attribution notices in `NOTICE`.

Copyright (c) 2026 Cyber Dick Lang

---

## ❤️ 支持与关注 / Support & Follow

> 开源代码可以免费，但显卡、电费、服务器和咖啡豆暂时还没学会开源。

你好，我是**赛博迪克朗**。我平时给 AI 喂提示词、给 ComfyUI 接管线，也负责修复那些“昨天明明还能跑”的神秘问题。教程里看起来三分钟解决的事，背后往往是三十次失败和一句又一句“这不应该啊”。

如果这个项目帮你少踩了一个坑、少重装了一次环境，那些和报错窗口深情对视的夜晚就算没有白熬。欢迎通过下面的方式支持和关注：

- [💙 支付宝 / Alipay](https://github.com/whmc76/.github/blob/main/SUPPORT.md#alipay)
- [🌍 PayPal](https://paypal.me/CyberDickLang)
- [📺 哔哩哔哩 / Bilibili](https://space.bilibili.com/339984)
- [▶️ YouTube](https://www.youtube.com/@CyberDickLang)

抖音、小红书、快手、今日头条、微信视频号、X：搜索全网统一名称 **“赛博迪克朗”**。

**不赞助也完全没关系。** 使用、Star、反馈、分享，甚至一句“这东西真能用”，都是继续更新的动力。谢谢你让这个项目不只是躺在我的硬盘里感动自己。
