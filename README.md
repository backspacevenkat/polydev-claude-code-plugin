# Polydev for Claude Code, Codex, Cursor and Gemini CLI

Ask several other AI models (GPT, Gemini, Grok and more) the same question from your coding agent,
and compare the answers. Useful for a second opinion on a bug, a design choice or a code review.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

There are two ways to run it:

- **Hosted** (`polydev-hosted`): nothing to install. The agent connects to `https://polydev.ai/mcp`
  and you sign in to Polydev in the browser the first time.
- **Local** (`polydev`): runs the npm client on your machine (Node.js 20 or newer), so it can also
  use the AI CLIs you are already signed in to, such as Claude Code, Codex and Gemini CLI.

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

| Tool | What it does |
|------|--------------|
| `get_perspectives` | Sends your prompt to the models set up in your Polydev account and returns each answer |
| `search_x` | Searches recent posts on X (read-only) |
| `rank_perspectives` | Records which answer helped most |

The plugin's slash command `/polydev-hosted:ask <question>` (or `/polydev:ask` for the local version)
gathers the relevant context, calls `get_perspectives` and summarises where the models agree and differ.
The agent calls Polydev only when you ask for it or agree to it.

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
