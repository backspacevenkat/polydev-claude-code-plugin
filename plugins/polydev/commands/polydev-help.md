# /polydev-help - Polydev Setup Guide

Display setup instructions and usage information for Polydev multi-model consultation.

## Response

Show the user this information:

---

# 🚀 Polydev - Multi-Model AI Consultation

**Get unstuck faster by consulting GPT, Gemini, and Grok alongside Claude.**

## Quick Setup

### 1. Get Your Free Token
Visit **[polydev.ai/dashboard/mcp-tokens](https://polydev.ai/dashboard/mcp-tokens)** to get your free API token.
- 1,000 messages/month free
- No credit card required

### 2. Add Your Token
Add to your shell profile (`~/.zshrc` or `~/.bashrc`):

```bash
export POLYDEV_USER_TOKEN="pd_your_token_here"
```

Then restart your terminal or run `source ~/.zshrc`

### 3. Restart Claude Code
Run `/mcp` to verify Polydev is connected - you should see "polydev" in the list.

## Commands

| Command | Description |
|---------|-------------|
| `/perspectives` | Get multi-model perspectives on your current problem |
| `/polydev-help` | Show this setup guide |

## Usage Examples

**When debugging:**
> "I'm stuck on this authentication bug. Use polydev to get different perspectives."

**For architecture decisions:**
> "Should I use Redis or PostgreSQL for caching? Get polydev perspectives."

**For code review:**
> "Review this authentication code for security issues using polydev."

## Troubleshooting

**MCP server not showing?**
1. Make sure `POLYDEV_USER_TOKEN` is set: `echo $POLYDEV_USER_TOKEN`
2. Restart Claude Code completely
3. Run `/mcp` to check status

**Token not working?**
- Tokens start with `pd_` - make sure you copied the full token
- Get a new token at [polydev.ai/dashboard/mcp-tokens](https://polydev.ai/dashboard/mcp-tokens)

## Research

Polydev's multi-model technique achieved **74.6% on SWE-bench Verified**, matching Claude Opus at 62% lower cost.

📄 [Read the research paper](https://polydev.ai/articles/swe-bench-paper)

---
