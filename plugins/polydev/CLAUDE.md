# Polydev Plugin for Claude Code

Multi-model AI consultation that helps you get unstuck faster by querying GPT-5, Gemini, Grok, and GLM simultaneously.

## Quick Setup (One Command!)

```bash
# Full setup - opens browser, auto-saves token, detects CLI tools
npx polydev-ai
```

That's it! The setup wizard will:
1. ✅ Open browser for one-click authentication
2. ✅ Auto-save your token (no manual copying!)
3. ✅ Detect installed AI CLI tools
4. ✅ Show what's ready to use

After setup, restart Claude Code.

## Commands

| Command | Description |
|---------|-------------|
| `/polydev [question]` | Get multi-model AI perspectives |
| `/polydev-login` | Authenticate via browser |
| `/polydev-auth` | Check auth status, credits, and CLI tools |
| `/perspectives` | Alias for `/polydev` |
| `/polydev-help` | Show usage guide |

## What's Available

### 🔧 Local AI Tools (FREE!)
If you have these installed, Polydev uses them first (no API credits!):
- **Claude Code** - Anthropic's Claude CLI
- **Codex CLI** - OpenAI's code AI
- **Gemini CLI** - Google's AI CLI
- **Aider** - AI pair programming

### ☁️ API Models (Uses Credits)
When local tools aren't available, or for multi-model perspectives:
- **GPT-5 Mini** - OpenAI's efficient model
- **Gemini 3 Flash** - Google's fast reasoning
- **Grok 4.1 Fast** - xAI's quick inference
- **GLM-4.7** - Zhipu AI's flagship

## Auto-Invocation Guidelines

**Claude should automatically invoke Polydev WITHOUT asking when:**

### ✅ Auto-Invoke When:

1. **User mentions being "stuck" or "confused"**
   - "I'm stuck on this bug"
   - "I can't figure out why this isn't working"

2. **User asks comparison/choice questions**
   - "Should I use X or Y?"
   - "Which is better..."
   - "What's the best approach for..."

3. **User requests code review or security check**
   - "Review this code"
   - "Check for security issues"

4. **User is debugging with multiple failed attempts**
   - After 2-3 unsuccessful debugging attempts

5. **User asks about architecture or design patterns**
   - "How should I structure..."
   - "What pattern should I use..."

### ❌ Do NOT Auto-Invoke When:

1. Simple syntax fixes or typos
2. Straightforward documentation lookups
3. User explicitly wants only Claude's opinion
4. Boilerplate code generation

## Pricing

| Tier | Credits/month | Cost |
|------|---------------|------|
| Free | 500 | $0 |
| Premium | 10,000 | $10/month |

**Pro Tip:** Install local CLI tools to use them for FREE and save your API credits!

## Support

- Dashboard: [polydev.ai/dashboard](https://polydev.ai/dashboard)
- Models: [polydev.ai/dashboard/models](https://polydev.ai/dashboard/models)
- Docs: [polydev.ai/docs](https://polydev.ai/docs)
