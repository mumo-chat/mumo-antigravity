# mumo — Google Antigravity plugin

**Multi-model deliberation panel for Google Antigravity.** When your agent is about to make an architecture choice, design tradeoff, or security-sensitive change worth checking across labs, mumo runs a panel of frontier models in parallel — Claude, GPT, Grok, DeepSeek, Kimi, and more — and returns each model's full response plus typed cross-model reactions: what each model keeps, challenges, or wants explored in the others' claims.

## What's in the box

- **`plugin.json`** — Antigravity plugin manifest (name, version, display metadata, suggested prompts).
- **`mcp_config.json`** — mumo MCP server config (Streamable HTTP against `https://mumo.chat/api/mcp/oauth` with browser OAuth sign-in; loads the four core deliberation tools eagerly and utility tools lazily).
- **`skills/mumo/SKILL.md`** — the canonical skill teaching Antigravity how to use mumo: when to invoke, the deliberation loop (create → wait → read → summarize → append/stop), how to read reactions, how to write your own, and when to verify session creation.
- **`skills/mumo/playbooks/`** — cognitive-shape playbooks loaded on demand: `contested-decision`, `design-review`, `uncertainty-expansion`, `red-team`.
- **`skills/mumo/references/`** — reference docs: `reading-reactions`, `writing-reactions`, `model-selection`, `synthesis`, `takeaway`, `operating-notes`.
- **`assets/logo.png`** — mumo plugin icon.

## Install

### 1. Install the plugin with Antigravity CLI

```bash
agy plugin install https://github.com/mumo-chat/mumo-antigravity
```

This unpacks the plugin into `~/.gemini/config/plugins/mumo` and registers both the mumo MCP server and the `mumo` skill.

### 2. Sign in to mumo

Start an `agy` session, open the plugin manager with `/plugin`, expand `mumo` under **Installed**, and choose **Sign in**.

1. Your browser opens to **Connect Google Antigravity to mumo** — confirm your mumo account and click **Continue**.
2. On the consent screen, click **Allow access**.
3. On the Antigravity confirmation page, copy the authorization code and paste it back into `agy`.

No API key is required. Installing and signing in once from `agy` also connects the Antigravity Desktop app — no second sign-in needed.

To disconnect later, remove **Google Antigravity** under **Settings → API Keys → Connected apps** at [mumo.chat/settings/api-keys](https://mumo.chat/settings/api-keys).

### 3. Verify with a free call

Before running a full deliberation, smoke-test the connection with a read-only call (no credit consumed). Ask Antigravity:

> Ask mumo to list available models.

That hits `list_models` over your signed-in connection. Getting your plan's model list back confirms the OAuth grant is active and the mumo tools (`create_deliberation`, `ask_a_model`, `wait_for_round`, `append_round`, `get_session`, `share_session`, `list_sessions`, `list_models`, `get_credit`) are reachable.

## Using the panel

Name `mumo` explicitly the first time so Antigravity routes through the panel instead of answering directly:

> Ask mumo to compare Postgres and MongoDB for our event store given 50k events/day, a Postgres-experienced team, and a 3-month runway. What would we regret 6 months in?

When you omit a model list, mumo automatically seats models from other labs — Claude, GPT, Kimi, and more — so you get independent perspectives alongside Gemini. Antigravity calls `create_deliberation`, then `wait_for_round`, reads the grouped reactions first, summarizes the round with a link to the session on `mumo.chat`, and only appends another round when you agree.

## When mumo is worth the latency tax

- Architecture decisions with non-obvious tradeoffs
- Plan or design review before commitment
- Pre-launch pressure tests
- Stuck debugging after repeated failed attempts
- Pre-commit adversarial review on risky diffs (auth, payments, migrations)
- Strategy questions with multiple defensible framings
- Explicit user requests

Skip mumo for routine refactors, formatting, syntax help, or anything where writing a test is cheaper than a panel.

## Links

- Product — https://mumo.chat
- Install guide — https://mumo.chat/install/antigravity
- MCP reference — https://mumo.chat/docs/mcp
- REST API — https://mumo.chat/docs/api
- Issues — https://github.com/mumo-chat/mumo-antigravity/issues

## License

MIT
