# mumo — Google Antigravity plugin

**Multi-model deliberation panel for Google Antigravity.** When your agent is about to make an architecture choice, design tradeoff, or security-sensitive change worth checking across labs, mumo runs a panel of frontier models in parallel — Claude, GPT, Grok, DeepSeek, Kimi, and more — and returns each model's full response plus typed cross-model reactions: what each model keeps, challenges, or wants explored in the others' claims.

## Requirements

- Google Antigravity (the Desktop app or the `agy` CLI).
- A Google account. Your first sign-in creates your mumo account, with free credit each month.
- mumo is available in the United States and Canada, excluding Quebec.

## Your data

Sessions run through this plugin are used only to answer your request. They are not used for Platform Improvement or Dataset Contribution. See the [Privacy Policy](https://mumo.chat/legal/privacy) and the [providers that serve each model](https://mumo.chat/legal/providers).

## Install

### In the Antigravity Desktop app

1. Install **mumo** from the Marketplace: in the app under **Customizations → Marketplace**, or with **Open in Antigravity** on the [Marketplace page](https://antigravity.google/docs/marketplace/?q=mumo&source=partner#browse-marketplace-plugins).
2. Your browser opens to **Connect Google Antigravity to mumo**. Sign in with Google, click **Continue**, then **Allow access**.
3. On the Antigravity confirmation page, click **Copy to Clipboard**. Paste the code into the **Paste code** field on the plugin's **Accounts** tab and click **Submit**.

No API key and no terminal are needed. To sign in again later, open the mumo plugin page, go to **Accounts**, choose **Sign out** if it shows as connected, then **Sign in**.

### With the Antigravity CLI

```bash
agy plugin install mumo@antigravity-plugins-partners
```

Then start an `agy` session, open the plugin manager with `/plugin`, expand `mumo` under **Installed**, and choose **Sign in**. Complete the sign-in in your browser, copy the authorization code from the confirmation page, and paste it back into `agy`.

To install straight from this repository instead: `agy plugin install https://github.com/mumo-chat/mumo-antigravity`.

### Disconnecting

Choose **Sign out** on the plugin's **Accounts** tab, then remove **Google Antigravity** under **Settings → API Keys → Connected apps** at [mumo.chat/settings/api-keys](https://mumo.chat/settings/api-keys).

### Verify with a free call

Before running a full deliberation, smoke-test the connection with a read-only call (no credit consumed). Ask Antigravity:

> Ask mumo to list available models.

That hits `list_models` over your signed-in connection. Getting your plan's model list back confirms the OAuth grant is active and the mumo tools (`create_deliberation`, `ask_a_model`, `wait_for_round`, `append_round`, `get_session`, `share_session`, `list_sessions`, `list_models`, `get_credit`) are reachable.

Then try a quick single-model question. It is the fastest way to see mumo work:

> Ask mumo what GPT thinks of this plan.

That calls `ask_a_model` with one model from another lab and returns its answer in full.

## Updating and removing

In the Desktop app, update or reinstall mumo from **Customizations → Marketplace**. With the CLI, uninstall and install again:

```bash
agy plugin uninstall mumo
agy plugin install mumo@antigravity-plugins-partners
```

Your sign-in is kept. To remove the plugin, uninstall it in the Desktop app or run `agy plugin uninstall mumo`; to also revoke its access to your mumo account, remove **Google Antigravity** under Connected apps as described above.

## Using the panel

Name `mumo` explicitly the first time so Antigravity routes through the panel instead of answering directly:

> Ask mumo to compare Postgres and MongoDB for our event store given 50k events/day, a Postgres-experienced team, and a 3-month runway. What would we regret 6 months in?

When you omit a model list, mumo seats a default panel of models from other labs, so you get independent perspectives alongside Gemini. A free account's default panel has two models; name others, such as Kimi or Grok, to add them. Antigravity calls `create_deliberation`, then `wait_for_round`, reads the grouped reactions first, summarizes the round with a link to the session on `mumo.chat`, and only appends another round when you agree.

## When mumo is worth the latency tax

- Architecture decisions with non-obvious tradeoffs
- Plan or design review before commitment
- Pre-launch pressure tests
- Stuck debugging after repeated failed attempts
- Pre-commit adversarial review on risky diffs (auth, payments, migrations)
- Strategy questions with multiple defensible framings
- Explicit user requests

Skip mumo for routine refactors, formatting, syntax help, or anything where writing a test is cheaper than a panel.

## What's in the box

- **`plugin.json`** — Antigravity plugin manifest (name, version, display metadata, suggested prompts).
- **`mcp_config.json`** — mumo MCP server config (Streamable HTTP against `https://mumo.chat/api/mcp/oauth` with browser OAuth sign-in; loads the four core deliberation tools eagerly and utility tools lazily).
- **`skills/mumo/SKILL.md`** — the canonical skill teaching Antigravity how to use mumo: when to invoke, the deliberation loop (create → wait → read → summarize → append/stop), how to read reactions, how to write your own, and when to verify session creation.
- **`skills/mumo/playbooks/`** — cognitive-shape playbooks loaded on demand: `contested-decision`, `design-review`, `uncertainty-expansion`, `red-team`.
- **`skills/mumo/references/`** — reference docs: `reading-reactions`, `writing-reactions`, `model-selection`, `synthesis`, `takeaway`, `operating-notes`.
- **`assets/logo.png`** — mumo plugin icon.

## Links

- Product — https://mumo.chat
- Install guide — https://mumo.chat/install/antigravity
- MCP reference — https://mumo.chat/docs/mcp
- REST API — https://mumo.chat/docs/api
- Privacy Policy — https://mumo.chat/legal/privacy
- Terms of Service — https://mumo.chat/legal/terms
- Support — support@mumo.chat
- Issues — https://github.com/mumo-chat/mumo-antigravity/issues

## License

MIT
