# Changelog

## 0.9.0 — 2026-11-21

Coordinated client release rendered from the mumo-mcp 0.9.0 baseline. It goes with mumo MCP server 1.4.0.

- `wait_for_round` results are text only. The second line is `Action: <value>`, with the same five values as before, and the skill now tells the agent to branch on that line. The third line names the session and round. Under the header, each model that failed, was cut off, hit a cap or was cut short by its provider gets an `Issue:` line.
- New section, "Hand the wait to a subagent". Where the client supports subagents, the agent creates the round itself and has a subagent on the same model wait and read. The subagent hands back the round without the full answers, the points no model reacted to, and a short note on tone. It hands back only a finished round, and says so when it could not read the whole result.
- Refusals start with `Error: <code>`.
- `references/operating-notes.md` and `references/synthesis.md` updated to match.
- Setup notes: the note about Antigravity not showing structured results is gone, since results are text only now. A new note says to use the built-in `self` subagent for a delegated wait, because it is the one that can reach the mumo tools.

## 0.8.0 — 2026-11-21

Initial release. Google Antigravity plugin for mumo's MCP server, rendered from the `mumo-mcp` 0.8.0 baseline.

- `plugin.json` — Antigravity plugin manifest with display metadata, suggested prompts, and icon.
- `mcp_config.json` — Streamable HTTP connection to `https://mumo.chat/api/mcp/oauth` using browser OAuth sign-in (no API key required); marks `create_deliberation`, `ask_a_model`, `wait_for_round`, and `append_round` as eager tools while keeping read and utility tools lazy.
- `skills/mumo/SKILL.md` — canonical deliberation skill with Antigravity sign-in setup, tool registry naming (`mumo_mumo`), and runtime notes covering text-channel responses and large-output file spillover.
- `skills/mumo/playbooks/` — `contested-decision`, `design-review`, `uncertainty-expansion`, `red-team`.
- `skills/mumo/references/` — `reading-reactions`, `writing-reactions`, `model-selection`, `synthesis`, `takeaway`, `operating-notes`.
