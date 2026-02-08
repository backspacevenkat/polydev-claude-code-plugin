---
description: Get multi-model AI perspectives on any coding problem
argument-hint: Your question or problem
---

# /polydev-ask [question] - Get Multi-Model AI Perspectives

Query multiple AI models (GPT-5, Gemini, Grok, GLM) simultaneously to get diverse perspectives on any coding problem.

## Instructions

When the user runs `/polydev-ask [question]`, do the following:

1. **Extract the question**: Parse the argument after `/polydev-ask` as the question. If no question is provided, look at the recent conversation context.

2. **Enhance the question**: Add relevant context from:
   - Current file being worked on
   - Recent errors or debugging attempts
   - Project structure if relevant

3. **Check if MCP tools are available** by looking for `mcp__plugin_polydev_mcp__get_perspectives` in your tools.

### If MCP tools ARE available:

Call the perspectives tool:
```
mcp__plugin_polydev_mcp__get_perspectives({
  prompt: "The enhanced question with full context"
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
  -H "User-Agent: polydev-mcp/1.9.0" \
  -d '{
    "jsonrpc": "2.0",
    "method": "tools/call",
    "params": {
      "name": "get_perspectives",
      "arguments": {
        "prompt": "YOUR ENHANCED QUESTION HERE"
      }
    },
    "id": "1"
  }'
```

4. **Synthesize the response**:
   - Highlight areas of **consensus** (high confidence)
   - Note where models **differ** (needs consideration)
   - Provide actionable **recommendations**

## Example Usage

**User**: `/polydev-ask How should I structure my React state management?`

**Claude calls** (if MCP tools available):
```
mcp__plugin_polydev_mcp__get_perspectives({
  prompt: "How should I structure state management in a React application? I'm building a dashboard with real-time updates, user preferences, and form state."
})
```

**Claude synthesizes**:
> **Multi-Model Perspectives on React State Management**
>
> **Consensus (High Confidence)**:
> - All models recommend separating server state (React Query/SWR) from client state
> - Zustand is favored for simplicity in medium-sized apps
>
> **Different Perspectives**:
> - GPT-5 emphasizes Redux Toolkit for large teams
> - Gemini recommends Jotai for atomic state
> - Grok suggests starting simple with useState + Context
>
> **Recommendation**: Start with Zustand for client state + React Query for server state.

## When to Use

- **Stuck debugging**: After 2-3 failed attempts
- **Architecture decisions**: Choosing between approaches
- **Code review**: Getting validation on implementation
- **Best practices**: Unsure about patterns

## Models Queried

All queries consult 4+ models in parallel:
- **GLM-4.7** - Zhipu AI's flagship model
- **Gemini 3** - Google's reasoning model
- **Grok 4.1** - xAI's inference model
- **GPT-5** - OpenAI's model
