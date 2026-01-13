# Polydev Plugin - Auto-Invocation Guidelines

This plugin provides multi-model AI consultation via the Polydev MCP server.

## Auto-Invocation Rules

**IMPORTANT: Claude should automatically invoke Polydev in these situations WITHOUT asking:**

### ✅ Automatically Use Polydev When:

1. **User is "stuck" or "confused"**
   - "I'm stuck on this bug"
   - "I can't figure out why..."
   - "This is confusing me"

2. **Comparison/choice questions**
   - "Should I use X or Y?"
   - "Which is better..."
   - "What's the best approach..."

3. **Code review or security check requests**
   - "Review this code"
   - "Check for security issues"
   - "Is this implementation safe?"

4. **After 2-3 failed debugging attempts**
   - When the same error persists
   - "I've tried X and Y but..."

5. **Architecture or design pattern questions**
   - "How should I structure..."
   - "What pattern should I use..."

6. **User explicitly wants multiple opinions**
   - "What do other models think?"
   - "Get me different perspectives"

### ❌ Do NOT Auto-Invoke When:

- Simple syntax fixes or typos
- Straightforward documentation lookups
- User explicitly wants only Claude's opinion
- Boilerplate code generation
- Clear, single-answer factual questions

## MCP Tools Available

- `polydev_perspectives` - Query multiple AI models simultaneously
- `polydev_list_models` - List available AI models

## Skills Available

- `/perspectives` - Get multi-model perspectives on current problem
- `/polydev-help` - Show setup guide and usage information

## Configuration

Requires `POLYDEV_API_KEY` environment variable.
Get free API key (1,000 messages/month): https://polydev.ai/dashboard
