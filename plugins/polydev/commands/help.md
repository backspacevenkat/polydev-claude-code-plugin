---
description: Polydev setup guide - commands and usage
---

# /polydev:help - Polydev Setup and Usage Guide

Show help for Polydev.

## Response Template

When the user runs `/polydev:help`, respond with:

---

## Polydev - Every AI model, inside the app you already use

Ask GPT, Claude, Gemini, Grok and more without leaving this session. Every answer says what paid for it.

### Quick Start

```bash
# 1. Sign in (opens the browser and saves the token)
/polydev:login

# 2. Ask a model
/polydev:ask have gpt-6.1-sol check this migration before I run it
```

### Commands

| Command | Description |
|---------|-------------|
| `/polydev:ask [question]` | Ask one model by name, several, or your default set |
| `/polydev:login` | Sign in through the browser |
| `/polydev:auth` | Check sign-in status and which sources are ready |
| `/polydev:help` | Show this help message |

### Examples

**One model:**
```
/polydev:ask have GPT check this migration before I run it
```

**Rewrite in plain English:**
```
/polydev:ask ask Claude to rewrite this error message in plain English
```

**Compare models:**
```
/polydev:ask ask GPT and Gemini whether to store sessions in Redis or Postgres, then tell me where they disagree
```

**Make an image (local version):**
```
Make a 1200x630 cover for this post with Nano Banana
```

### What pays

Each answer has a "Paid by" line. In this local version, one of these pays:
- your ChatGPT plan, after Continue with ChatGPT (`connect_chatgpt_plan`), with a weekly cap you set in ChatGPT;
- the Claude Code or Codex CLI you are signed in to on this machine, under your own login;
- your own API keys or OpenRouter key, added at [polydev.ai/dashboard/models](https://polydev.ai/dashboard/models);
- Polydev's 10 free requests.

`list_models` shows which models you can reach and what pays for each.

### Support

- Dashboard: [polydev.ai/dashboard](https://polydev.ai/dashboard)
- Docs: [polydev.ai/docs](https://polydev.ai/docs)
- Email: support@polydev.ai

---
