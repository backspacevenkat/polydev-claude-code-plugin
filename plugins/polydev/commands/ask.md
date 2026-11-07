---
description: Ask another AI model (or several) through Polydev
argument-hint: Your question, optionally naming a model (for example gpt-6.1-sol)
---

# /polydev:ask [question] - Ask another AI model

Send the user's question to another AI model (such as GPT, Claude, Gemini or Grok) through Polydev and
show the answer. Every answer says what paid for it.

## Instructions

When the user runs `/polydev:ask [question]`, do the following:

1. **Take the question**: use the argument as the question. If there is none, use the problem being discussed.

2. **Pick the model**:
   - The user names one model (for example "gpt-6.1-sol" or "ask Claude"): pass it as `model`.
   - The user names several: pass them as `models`.
   - The user names none: pass neither, and their default set is asked.
   - `mcp__plugin_polydev_mcp__list_models` shows which models they can reach and what pays for each.

3. **Add context**: include only what the model needs (the relevant code, the error, constraints). Leave out
   secrets, keys and unrelated files: Polydev passes the prompt to other model providers.

4. **Check if MCP tools are available** by looking for `mcp__plugin_polydev_mcp__ask_model` in your tools.

### If MCP tools ARE available:

```
mcp__plugin_polydev_mcp__ask_model({
  prompt: "The question with the context it needs",
  model: "gpt-6.1-sol"   // optional; or models: a list of names; omit both for the default set
})
```

### If MCP tools are NOT available (Cowork / sandboxed environments):

Use curl to call the Polydev API directly:
```bash
# Load token if not in env
[ -z "$POLYDEV_USER_TOKEN" ] && [ -f "$HOME/.polydev.env" ] && source "$HOME/.polydev.env"

if [ -z "$POLYDEV_USER_TOKEN" ]; then
  echo "Not authenticated. Run /polydev:login first."
  exit 1
fi

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

Add `"model": "gpt-6.1-sol"` (or `"models": [...]`) to `arguments` when the user named a model.

5. **Show the answer**:
   - Give each answer with its "Paid by" line.
   - If several models answered, say where they agree, where they differ, and what you recommend.

## Example

**User**: `/polydev:ask have gpt-6.1-sol check this migration before I run it`

**Claude calls**:
```
mcp__plugin_polydev_mcp__ask_model({
  prompt: "Check this Postgres migration before I run it on production: <migration SQL>. Look for locking, data loss and missing rollbacks.",
  model: "gpt-6.1-sol"
})
```

**Claude replies** with GPT's findings, the "Paid by" line, and what to change before running it.

## What pays

Each answer says what paid for it: the user's ChatGPT plan (after `connect_chatgpt_plan`), the Claude Code
or Codex CLI they are signed in to on this machine, their own API keys or OpenRouter key, or Polydev's
10 free requests.
