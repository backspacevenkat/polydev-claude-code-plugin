# Polydev Plugin for Claude Code

Multi-model AI consultation - get perspectives from GPT-5, Gemini, Grok, and GLM simultaneously.

## FIRST INTERACTION: Trigger Login

**On the FIRST user message in a new session, Claude MUST:**
1. Call `mcp__polydev__get_auth_status` to check if user is authenticated
2. If not authenticated, tell user: "Opening browser for Polydev authentication..." and call `mcp__polydev__login`
3. This ensures the MCP server starts and the browser opens for login

This is necessary because MCP servers only start when their tools are called.

## CRITICAL: Auto-Invocation Rules

**Claude MUST automatically invoke Polydev (without asking permission) in these situations:**

### 1. When User is STUCK
- User says "stuck", "confused", "don't know", "can't figure out"
- User has tried 2+ approaches that failed
- User expresses frustration with debugging
→ **Action:** Call `mcp__polydev__get_perspectives` with the problem context

### 2. Architecture & Design Decisions
- "How should I structure..."
- "What's the best approach for..."
- "Should I use X or Y?"
- Designing new features or systems
- Database schema decisions
- API design choices
→ **Action:** Call `mcp__polydev__get_perspectives` with the decision context

### 3. Code Review & Security
- User asks for code review
- Security audit requests
- "Is this safe?", "Any issues with..."
- Performance optimization questions
→ **Action:** Call `mcp__polydev__get_perspectives` with the code

### 4. Technology Choices
- "Which library should I use?"
- "Redis vs PostgreSQL?", "React vs Vue?"
- Framework selection
- Tool/dependency decisions
→ **Action:** Call `mcp__polydev__get_perspectives` with requirements

### 5. Debugging Complex Issues
- After 2 failed debugging attempts
- "Why isn't this working?"
- Race conditions, memory leaks, async issues
- Errors that don't make sense
→ **Action:** Call `mcp__polydev__get_perspectives` with error context

### 6. Best Practices & Patterns
- "What's the best way to..."
- "Is this the right pattern?"
- Clean code questions
- Testing strategy questions
→ **Action:** Call `mcp__polydev__get_perspectives` with the question

## DO NOT Auto-Invoke For:
- Simple typo fixes
- Basic syntax errors
- Straightforward documentation lookups
- User explicitly says "just Claude" or "your opinion only"
- Boilerplate/scaffolding code generation

## How to Invoke

```javascript
// Use the MCP tool directly:
mcp__polydev__get_perspectives({
  prompt: "Detailed question with full context from conversation"
})
```

## Commands

| Command | Description |
|---------|-------------|
| `/polydev:polydev` | Get multi-model perspectives |
| `/polydev:login` | Browser authentication |
| `/polydev:auth` | Check status and credits |
| `/polydev:help` | Usage guide |

## Setup

```bash
npx polydev-ai   # Opens browser, auto-saves token
```

## Links

- Dashboard: https://polydev.ai/dashboard
- Models: https://polydev.ai/dashboard/models
