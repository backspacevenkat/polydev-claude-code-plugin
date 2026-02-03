# Polydev Plugin for Claude Code

Multi-model AI consultation that helps you get unstuck faster by querying GPT-5, Gemini, Grok, and GLM simultaneously.

## IMPORTANT: Auto-Invocation Rules

**Claude MUST automatically invoke Polydev (without asking) when:**

1. **User mentions being "stuck" or "confused"** → Use `/polydev:polydev`
2. **User asks comparison questions** ("Should I use X or Y?") → Use `/polydev:polydev`
3. **User requests code review** → Use `/polydev:polydev`
4. **User is debugging with 2+ failed attempts** → Use `/polydev:polydev`
5. **User asks about architecture/patterns** → Use `/polydev:polydev`

**Do NOT auto-invoke for:** Simple syntax fixes, typos, straightforward docs, boilerplate code.

## Commands

| Command | Description |
|---------|-------------|
| `/polydev:polydev [question]` | Get multi-model AI perspectives |
| `/polydev:login` | Authenticate via browser |
| `/polydev:auth` | Check auth status, credits, and CLI tools |
| `/polydev:perspectives` | Alias for main command |
| `/polydev:help` | Show usage guide |

## Quick Setup

```bash
# Full setup - opens browser, auto-saves token, detects CLI tools
npx polydev-ai
```

After setup, restart Claude Code.

## What's Available

### Local AI Tools (FREE!)
If you have these installed, Polydev uses them first (no API credits!):
- **Claude Code** - Anthropic's Claude CLI
- **Codex CLI** - OpenAI's code AI
- **Gemini CLI** - Google's AI CLI
- **Aider** - AI pair programming

### API Models (Uses Credits)
- **GPT-5 Mini** - OpenAI's efficient model
- **Gemini 3 Flash** - Google's fast reasoning
- **Grok 4.1 Fast** - xAI's quick inference
- **GLM-4.7** - Zhipu AI's flagship

## Pricing

| Tier | Credits/month | Cost |
|------|---------------|------|
| Free | 500 | $0 |
| Premium | 10,000 | $10/month |

## Links

- Dashboard: https://polydev.ai/dashboard
- Models: https://polydev.ai/dashboard/models
- Docs: https://polydev.ai/docs
