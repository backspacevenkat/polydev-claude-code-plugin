---
name: second-opinion
description: When and how to ask other AI models (GPT, Gemini, Grok and more) for a second opinion through Polydev. Use when the user asks for other models' views, or when offering one would clearly help with a stuck bug, a design trade-off or a review.
---

# Second opinion with Polydev

Polydev asks the models set up in the user's Polydev account the same question and returns each answer.
Its tools come from this plugin's MCP server (`mcp__plugin_polydev_mcp__*`). If they are missing (for
example in a sandbox without npm access), use the curl fallback below or `/polydev:login`.

## When to use it

Polydev sends the prompt it is given to other model providers, so call it only when the user asks for it
(for example "ask other models", "get a second opinion", `/polydev:ask`) or agrees when you offer.

You may **offer** a second opinion, without calling the tool, when it would clearly help:
- the user is stuck or two approaches have already failed;
- an architecture, design or technology choice with real trade-offs;
- a code review or security question where independent views help.

Ask first, for example: "Want me to ask a few other models through Polydev?" Call
`mcp__plugin_polydev_mcp__get_perspectives` once the user says yes. Include only the context the question
needs; leave out secrets, keys and unrelated code.

## Curl fallback for get_perspectives (when MCP tools unavailable)

If MCP tools are not available but the user has authenticated:

```bash
# Load token if not in env
[ -z "$POLYDEV_USER_TOKEN" ] && [ -f "$HOME/.polydev.env" ] && source "$HOME/.polydev.env"

curl -s -X POST "https://www.polydev.ai/api/mcp" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $POLYDEV_USER_TOKEN" \
  -H "User-Agent: polydev-mcp/1.9.0" \
  -d '{
    "jsonrpc": "2.0",
    "method": "tools/call",
    "params": {
      "name": "get_perspectives",
      "arguments": {
        "prompt": "YOUR QUESTION HERE"
      }
    },
    "id": "1"
  }'
```

## After the answers come back

Summarise where the models agree, where they differ, and what you recommend. Setup and sign-in:
`/polydev:login` (or `npx -p polydev-ai polydev-login`).
