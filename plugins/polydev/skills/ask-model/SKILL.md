---
name: ask-model
description: When and how to ask another AI model (GPT, Claude, Gemini, Grok and more) through Polydev. Use when the user asks for another model by name or asks to compare models, or when offering one would clearly help with a stuck bug, a design trade-off or a review.
---

# Ask another model with Polydev

Polydev sends a prompt to the model the user picks, or to their default set, and returns each answer with
the line "Paid by: ..." (their ChatGPT plan, the Claude Code or Codex CLI they are signed in to on this
machine, their own API keys or OpenRouter key, or Polydev's free requests).
Its tools come from this plugin's MCP server (`mcp__plugin_polydev_mcp__*`). If they are missing (for
example in a sandbox without npm access), use the curl fallback below or `/polydev:login`.

## When to use it

Polydev sends the prompt it is given to other model providers, so call it only when the user asks for it
(for example "ask GPT", "have gpt-6.1-sol check this", "ask GPT and Gemini and compare", `/polydev:ask`)
or agrees when you offer.

You may **offer** to ask another model, without calling the tool, when it would clearly help:
- the user is stuck or two approaches have already failed;
- an architecture, design or technology choice with real trade-offs;
- a code review or security question where an independent check helps.

Ask first, for example: "Want me to ask GPT about this through Polydev?" Call
`mcp__plugin_polydev_mcp__ask_model` once the user says yes.

## How to call it

- One model named: pass `model` (for example `"gpt-6.1-sol"`).
- Several named: pass `models` (a list).
- None named: pass neither; the user's default set is asked.
- Unsure what is available: `mcp__plugin_polydev_mcp__list_models` lists the models and what pays for each.
- The user wants their ChatGPT plan to pay for OpenAI models: `mcp__plugin_polydev_mcp__connect_chatgpt_plan`
  (Continue with ChatGPT), then `chatgpt_plan_status` to check.

Include only the context the question needs; leave out secrets, keys and unrelated code.
`get_perspectives` is the older name of `ask_model` and behaves the same.

## Curl fallback for ask_model (when MCP tools are unavailable)

If MCP tools are not available but the user has authenticated:

```bash
# Load token if not in env
[ -z "$POLYDEV_USER_TOKEN" ] && [ -f "$HOME/.polydev.env" ] && source "$HOME/.polydev.env"

curl -s -X POST "https://www.polydev.ai/api/mcp" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $POLYDEV_USER_TOKEN" \
  -H "User-Agent: polydev-mcp/1.12.0" \
  -d '{
    "jsonrpc": "2.0",
    "method": "tools/call",
    "params": {
      "name": "ask_model",
      "arguments": {
        "prompt": "YOUR QUESTION HERE"
      }
    },
    "id": "1"
  }'
```

Add `"model"` or `"models"` to `arguments` when the user named a model.

## After the answers come back

Show each answer with its "Paid by" line. If several models answered, say where they agree, where they
differ, and what you recommend. Setup and sign-in: `/polydev:login` (or `npx -p polydev-ai polydev-login`).
