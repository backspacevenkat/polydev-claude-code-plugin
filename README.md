# Polydev Plugin for Claude Code

🚀 **Multi-model AI consultation for Claude Code** - Get perspectives from Claude, GPT, Gemini, Grok, and Z AI in your IDE.

[![SWE-bench](https://img.shields.io/badge/SWE--bench-74.6%25-green)](https://polydev.ai/articles/swe-bench-paper)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## What is Polydev?

Polydev lets you consult multiple AI models simultaneously when you're stuck on bugs, making architecture decisions, or reviewing code. Different models catch different things - combining their perspectives eliminates blind spots.

**Stop copy-pasting your code into ChatGPT, Claude, Gemini, Grok...** Get all their perspectives in your IDE with one request.

**Research**: Achieved 74.6% on SWE-bench Verified, matching Claude Opus at 62% lower cost.

## Installation

```bash
# Add the Polydev marketplace
/plugin marketplace add backspacevenkat/polydev-claude-code-plugin

# Install the plugin
/plugin install polydev
```

## Setup

1. **Get your free token** at [polydev.ai/dashboard](https://polydev.ai/dashboard)
   - 1,000 messages/month free
   - No credit card required

2. **Add token to your environment:**
   ```bash
   export POLYDEV_USER_TOKEN="pd_your-token-here"
   ```

3. **Restart Claude Code** and verify with `/mcp`

## Usage

### Slash Commands

| Command | Description |
|---------|-------------|
| `/perspectives` | Get multi-model perspectives on current problem |
| `/polydev-help` | Show setup guide |

### Natural Language

Just ask Claude - it will automatically invoke Polydev when appropriate:

```
"I'm stuck on this authentication bug. Get different perspectives."

"Should I use Redis or PostgreSQL for session storage?"

"Review this API endpoint for security issues using polydev."
```

### Auto-Invocation

The plugin automatically triggers multi-model consultation when you:
- Say you're "stuck" or "confused"
- Ask comparison questions ("Should I use X or Y?")
- Request code reviews or security checks
- Have multiple failed debugging attempts

## Models Available

Polydev queries multiple leading AI models simultaneously:

| Model | Provider |
|-------|----------|
| Claude | Anthropic |
| GPT | OpenAI |
| Gemini | Google |
| Grok | xAI |
| Z AI | Zhipu |

## Example Output

```
🤖 Multi-Model Analysis

Claude's Perspective:
The N+1 query pattern here is causing performance issues...

GPT's Perspective:
The infinite re-render is likely caused by object recreation in deps array...

Gemini's Perspective:
Check for setState calls directly in the component body...

Grok's Perspective:
Consider using useCallback for function dependencies...

✅ Consensus: All models agree the issue is in the dependency array
💡 Recommendation: Use useMemo/useCallback for object/function deps
```

## Links

- 🌐 [Polydev Website](https://polydev.ai)
- 📄 [Research Paper](https://polydev.ai/articles/swe-bench-paper)
- 📚 [Claude Code Guide](https://polydev.ai/articles/claude-code-guide)
- 💬 [Support](mailto:support@polydev.ai)

## License

MIT License - see [LICENSE](LICENSE)
