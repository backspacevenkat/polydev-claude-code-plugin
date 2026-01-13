# /perspectives - Get multi-model AI perspectives

When the user runs this command, use the Polydev MCP server to consult multiple AI models (GPT, Gemini, Grok) about the current problem or question.

## Instructions

1. Identify the user's current problem or question from the conversation context
2. Call `polydev.getPerspectives()` with a detailed description of the issue
3. Synthesize the responses into actionable recommendations
4. Highlight where models agree and where they differ
5. Provide a final recommendation based on consensus

## Example Usage

User: /perspectives
(Claude will analyze the current context and get multi-model feedback)

User: /perspectives Should I use Redis or PostgreSQL for caching?
(Claude will query multiple models about this specific question)

## Response Format

Present the multi-model insights in this structure:

### 🤖 Multi-Model Analysis

**GPT's Perspective:**
[Summary of GPT's response]

**Gemini's Perspective:**
[Summary of Gemini's response]

**Grok's Perspective:**
[Summary of Grok's response]

### ✅ Consensus Points
- [Where all models agree]

### ⚖️ Different Approaches
- [Where models suggest different solutions]

### 💡 Recommendation
[Your synthesized recommendation based on the perspectives]
