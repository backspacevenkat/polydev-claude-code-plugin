---
description: Check Polydev authentication status and credits
---

# /polydev-auth - Check Status

Check your Polydev authentication status, credits, and available tools.

## Instructions

When the user runs `/polydev-auth`:

### Step 1: Check if MCP tools are available

Look for tools starting with `mcp__plugin_polydev_polydev__` in your available tools list.

### Step 2a: If MCP tools ARE available

Call the `get_auth_status` tool:
```
mcp__plugin_polydev_polydev__get_auth_status({})
```

### Step 2b: If MCP tools are NOT available (Cowork / sandboxed environments)

Check authentication status via bash:

```bash
# Check if token exists
if [ -n "$POLYDEV_USER_TOKEN" ]; then
  # Verify token with the server
  RESULT=$(curl -s -X POST "https://www.polydev.ai/api/mcp" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $POLYDEV_USER_TOKEN" \
    -d '{"action": "check_status"}')
  echo "$RESULT" | python3 -m json.tool 2>/dev/null || echo "$RESULT"
elif [ -f "$HOME/.polydev.env" ]; then
  # Try loading from file
  source "$HOME/.polydev.env"
  if [ -n "$POLYDEV_USER_TOKEN" ]; then
    RESULT=$(curl -s -X POST "https://www.polydev.ai/api/mcp" \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer $POLYDEV_USER_TOKEN" \
      -d '{"action": "check_status"}')
    echo "$RESULT" | python3 -m json.tool 2>/dev/null || echo "$RESULT"
  else
    echo "No token found. Run /polydev:login to authenticate."
  fi
else
  echo "Not authenticated. Run /polydev:login to authenticate."
fi
```

### Step 3: Display the results

Show the user:
- Authentication status (connected/not connected)
- Account email
- Credits remaining
- Subscription tier
- If not authenticated, suggest running `/polydev:login`

## Example

**User**: `/polydev-auth`

**If authenticated**:
> Polydev Status
>
> Authenticated: Yes
> Account: user@example.com
> Credits: 9,500
> Tier: Premium
>
> Dashboard: https://polydev.ai/dashboard

**If not authenticated**:
> Not authenticated.
>
> To login:
> 1. Use `/polydev:login`
> 2. Or run in terminal: `npx polydev-ai`

## Quick Links

- Dashboard: https://polydev.ai/dashboard
- Models: https://polydev.ai/dashboard/models
- Usage: https://polydev.ai/dashboard/usage
