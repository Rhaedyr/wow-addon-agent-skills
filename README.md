# WoW addon agent skills

Reusable **differential** agent skills for World of Warcraft addon work across:

| Pack | Use when |
| --- | --- |
| [`universal/`](universal/SKILL.md) | Shared Mainline 12.x rules (secrets, no CLEU, prefer `C_*`) |
| [`midnight/`](midnight/SKILL.md) | Midnight Standard (retail) specifics |
| [`forever/`](forever/SKILL.md) | WoW: Forever (Camelot) specifics vs Midnight |

These are **not** a full Lua API dump. For live signatures, diffs, linting, and TOC checks, use **[hated-wow-mcp](https://github.com/RdyGaming/hated-wow-mcp)** with `flavor: "mainline"` or `flavor: "forever"`.

## How to use in a new addon repo

1. Copy the relevant `*/SKILL.md` files (or the whole tree) into your project, e.g. `agent-skills/` and optionally `.cursor/skills/`.
2. Point `AGENTS.md` at them.
3. Install hated-wow-mcp in Cursor / Grok Bot and set `WOW_DEFAULT_FLAVOR` appropriately.
4. Forever **1.60.1** Interface is confirmed as **`16001`** (build 69913) — keep `forever/SKILL.md` and project TOCs in sync with live `GetBuildInfo()` dumps.

## Seeded from

Initial content came from [EventHorizon_Infall-Forever](https://github.com/Rhaedyr/EventHorizon_Infall-Forever) (`forever` branch), including a Forever compat scan under [`docs/FOREVER_COMPAT_REPORT.md`](docs/FOREVER_COMPAT_REPORT.md).

## Growing this repo

Prefer adding **rules that failed in real ports** (API moved, Forever-only gap, secret-value footgun) over copying encyclopedia pages. MCP `wow_api_diff` / `wow_lua_lint` results are good sources for new bullets.
