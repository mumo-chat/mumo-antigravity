# Changelog

## 0.8.0 — 2026-11-21

Initial release. Google Antigravity plugin for mumo's MCP server, rendered from the `mumo-mcp` 0.8.0 baseline.

- `plugin.json` — Antigravity plugin manifest with display metadata, suggested prompts, and icon.
- `mcp_config.json` — Streamable HTTP connection to `https://mumo.chat/api/mcp/oauth` using browser OAuth sign-in (no API key required); marks `create_deliberation`, `ask_a_model`, `wait_for_round`, and `append_round` as eager tools while keeping read and utility tools lazy.
- `skills/mumo/SKILL.md` — canonical deliberation skill with Antigravity sign-in setup, tool registry naming (`mumo_mumo`), and runtime notes covering text-channel responses and large-output file spillover.
- `skills/mumo/playbooks/` — `contested-decision`, `design-review`, `uncertainty-expansion`, `red-team`.
- `skills/mumo/references/` — `reading-reactions`, `writing-reactions`, `model-selection`, `synthesis`, `takeaway`, `operating-notes`.
