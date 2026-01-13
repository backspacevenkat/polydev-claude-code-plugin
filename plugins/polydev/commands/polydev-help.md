# /polydev-help - Polydev Setup Guide

Display setup instructions and usage information for Polydev multi-model consultation.

## Response

Show the user this information:

---

# 🚀 Polydev - Multi-Model AI Consultation

**Get unstuck faster by consulting GPT, Gemini, and Grok alongside Claude.**

## Setup

### 1. Get Your API Key (Free)
Visit [polydev.ai/dashboard](https://polydev.ai/dashboard) to get your free API key.
- 1,000 messages/month on the free plan
- No credit card required

### 2. Add Your API Key
Add to your environment or Claude Code settings:

```bash
export POLYDEV_API_KEY="your-api-key-here"
```

Or add to `~/.claude/settings.json`:
```json
{
  "mcpServers": {
    "polydev": {
      "env": {
        "POLYDEV_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

### 3. Restart Claude Code
Run `/mcp` to verify Polydev is connected.

## Available Commands

| Command | Description |
|---------|-------------|
| `/perspectives` | Get multi-model perspectives on current problem |
| `/polydev-help` | Show this help message |

## Usage Examples

**Debugging:**
> "I'm stuck on this authentication bug. Use polydev to get different perspectives."

**Architecture:**
> "Should I use Redis or PostgreSQL? Get polydev perspectives."

**Code Review:**
> "Review this code for security issues using polydev."

## Research

Polydev's multi-model technique achieved **74.6% on SWE-bench Verified**, matching Claude Opus at 62% lower cost.

📄 [Read the research paper](https://polydev.ai/articles/swe-bench-paper)

---
