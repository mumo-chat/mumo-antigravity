# Changelog

## 0.9.4 — 2026-11-28

- Replace the Marketplace `suggestedPrompts` with three round-starting prompts (a cold-start Postgres vs. MongoDB comparison, an open project decision review, and an adversarial architectural-risk challenge).

## 0.9.3 — 2026-11-27

- Marketplace description notes US & Canada availability up front (`US & Canada only.`).

## 0.9.2 — 2026-11-24

Skill notes for mumo MCP server 1.6.0.

- A failed model's line now shows its error code and a short sentence saying what happened, and a response that did not finish normally shows a short state. The skill's notes describe the new lines.
- A compact re-read shows the model and how it ended, without token counts.
- A result that begins `Error: internal_error` means mumo itself failed. The skill tells the agent to say so and not to change the arguments.
- A round's web link appears once, in the header.

## 0.9.1 — 2026-11-24

mumo is in the Antigravity Marketplace. This release rewrites the listing for people who find it there.

- Install leads with the Marketplace: a three-step flow in the Desktop app with no terminal, then `agy plugin install mumo@antigravity-plugins-partners` for the CLI. Installing from this repository still works.
- Requirements: a Google account is enough, and your first sign-in creates your mumo account. mumo is available in the United States and Canada, excluding Quebec.
- New "Your data" section: sessions run through this plugin are used only to answer your request.
- New description and a single-model suggested prompt. A quick single-model example follows the verify step.
- The default panel for a free account has two models; name others to add them.
- Skill setup: signing in again is described for the Desktop app's Accounts tab as well as the CLI, and a region refusal is relayed without a retry.
- Links to the Privacy Policy, Terms of Service and support.

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
