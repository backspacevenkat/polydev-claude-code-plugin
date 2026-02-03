# /polydev - Multi-Model AI Consultation

Query multiple AI models (GPT, Gemini, Grok) simultaneously to get diverse perspectives on coding problems.

## Usage

```
/polydev [your question]
```

## Instructions

When the user runs `/polydev` with a question:

1. **Use the Polydev MCP server** to call `mcp__polydev__get_perspectives` (or similar tool name)
   - Pass the user's question as the prompt
   - Include relevant context from the conversation

2. **If the MCP tool is not available**:
   - Check if `POLYDEV_USER_TOKEN` is set
   - If not, guide them to run `/polydev-login` or `/polydev-auth`

3. **Present the results** in a clear format showing each model's perspective

## Response Format

### 🤖 Multi-Model Analysis

**Your Question:** [user's question]

---

**GPT's Perspective:**
[Summary of GPT's response]

**Gemini's Perspective:**
[Summary of Gemini's response]

**Grok's Perspective:**
[Summary of Grok's response]

---

### ✅ Consensus Points
- [Where models agree]

### ⚖️ Different Approaches
- [Where models differ]

### 💡 Recommendation
[Synthesized recommendation based on all perspectives]

## Examples

```
/polydev Why is my React useEffect running twice?
/polydev Should I use Redis or PostgreSQL for session storage?
/polydev Review this authentication code for security issues
```

## Not Working?

If the Polydev MCP server isn't responding:
1. Run `/polydev-auth` to check authentication
2. Run `/mcp` to verify the server is connected
3. Run `/polydev-help` for troubleshooting
