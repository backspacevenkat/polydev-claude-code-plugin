---
description: Polydev setup guide - commands and usage
---

# /polydev-help - Polydev Setup and Usage Guide

Display help information about Polydev multi-model AI consultation.

## Response Template

When the user runs `/polydev-help`, respond with:

---

## Polydev - Multi-Model AI Consultation

Ask several other AI models the same question and compare their answers.

### Quick Start

```bash
# 1. Login (opens browser, auto-configures token)
/polydev-login

# 2. Use it
/polydev How should I structure my React state?
```

### Available Commands

| Command | Description |
|---------|-------------|
| `/polydev [question]` | Get multi-model AI perspectives on any problem |
| `/polydev-login` | Authenticate via browser (recommended) |
| `/polydev-auth` | Check authentication status |
| `/perspectives` | Alias for `/polydev` |
| `/polydev-help` | Show this help message |

### Usage Examples

**When debugging:**
```
/polydev I'm getting a TypeError in my React component when mapping over an array
```

**When choosing technologies:**
```
/polydev Should I use Redis or PostgreSQL for session storage?
```

**When reviewing code:**
```
/polydev Review this authentication flow for security issues
```

### How It Works

1. You describe your problem or question
2. Polydev asks the models set up in your account (your local CLIs, your own API keys, or the free allowance) in parallel; the current list is at [polydev.ai/docs](https://polydev.ai/docs)
3. You get synthesized insights showing:
   - Where models **agree** (high confidence)
   - Where models **differ** (needs consideration)
   - Actionable **recommendations**

### Cost

Polydev is free. Your own access pays for the tokens: the AI CLIs you are signed in to on this machine,
your own API keys, or a one-time allowance of 10 requests on Polydev's keys.

### Support

- Dashboard: [polydev.ai/dashboard](https://polydev.ai/dashboard)
- Docs: [polydev.ai/docs](https://polydev.ai/docs)
- Email: support@polydev.ai

---
