# Polydev for Claude Code, Codex, Cursor and Gemini CLI

Every AI model, inside the app you already use.

Ask GPT from Claude. Ask Claude from ChatGPT. Make an image with Nano Banana from Codex.

10 free requests to try. After that, your ChatGPT plan or your own API keys pay.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Switch models, not apps. Pick the model for each task: plan in Claude, have GPT check the migration,
make the cover image with Nano Banana. Every answer says what paid for it.

There are two ways to run it:

- **Hosted** (`polydev-hosted`): nothing to install. The app connects to `https://polydev.ai/mcp`
  and you sign in to Polydev in the browser the first time. Answers are paid by your own API keys,
  your OpenRouter key or Polydev's 10 free requests.
- **Local** (`polydev`): runs the npm client `polydev-ai` on your machine (Node.js 20 or newer). On top
  of the hosted options it can use your ChatGPT plan (Sign in with ChatGPT), run the Claude Code or
  Codex CLI you are already signed in to, and make images.

## Claude Code

```bash
/plugin marketplace add backspacevenkat/polydev-claude-code-plugin
/plugin install polydev-hosted@polydev-marketplace
```

Then run `/mcp`, choose `polydev` and sign in. For the local version, install
`polydev@polydev-marketplace` instead; its first call opens the browser to sign in.

Without the plugin:

```bash
claude mcp add --transport http polydev https://polydev.ai/mcp
```

## Codex

```bash
codex plugin marketplace add backspacevenkat/polydev-claude-code-plugin
codex plugin add polydev-hosted@polydev
```

Or add the server directly:

```bash
codex mcp add polydev --url https://polydev.ai/mcp
codex mcp login polydev
```

## Gemini CLI

```bash
gemini extensions install https://github.com/backspacevenkat/polydev-claude-code-plugin
```

Then run `/mcp auth polydev`.

## Cursor, VS Code, Windsurf, Claude and ChatGPT

See [polydev.ai/install](https://polydev.ai/install) for one-click links and the settings for each app.

## Tools

Hosted (`https://polydev.ai/mcp`):

| Tool | What it does |
|------|--------------|
| `ask_model` | Sends your prompt to one model or a list (for example `gpt-6.1-sol`), or to your default set if you name none, and returns each answer with what paid for it |
| `list_models` | Lists the models you can reach and what pays for each |
| `search_x` | Searches recent posts on X (read-only; needs your own xAI key) |
| `rank_perspectives` | Records which answer helped most |

`get_perspectives` still works as the older name of `ask_model`.

The local client (`polydev-ai` 1.12.0) has the same tools plus `get_auth_status`, `login`,
`chatgpt_plan_status`, `connect_chatgpt_plan` (Continue with ChatGPT, so your ChatGPT plan pays for
OpenAI models) and `generate_image`.

The slash command `/polydev-hosted:ask <question>` (or `/polydev:ask` for the local version) gathers the
relevant context and calls `ask_model`. Name a model to ask just that one; name several to compare them.
The app calls Polydev only when you ask for it or agree to it.

## Privacy

Prompts you send through Polydev are passed to the model providers you chose. Don't include secrets.
Disconnect an app at any time under [Connected apps](https://polydev.ai/dashboard/mcp-tokens).
See the [privacy policy](https://polydev.ai/privacy).

## Links

- [polydev.ai](https://polydev.ai)
- [Install guide](https://polydev.ai/install)
- [Support](mailto:support@polydev.ai)

## License

MIT, see [LICENSE](LICENSE).
