# /polydev-auth - Check Status

Check your Polydev authentication status, credits, and available tools.

## Instructions

When the user runs `/polydev-auth`:

1. **Call the get_auth_status MCP tool**:
   ```
   Use the polydev MCP server's "get_auth_status" tool
   ```

2. **Display the results** showing:
   - Authentication status
   - Account email
   - Credits remaining
   - Subscription tier
   - Available tools

## Example

**User**: `/polydev-auth`

**Claude uses the get_auth_status tool from polydev MCP server**

**If authenticated**:
> Polydev Status
> ────────────────────────────────────────
>
> Authenticated: Yes
> Account: user@example.com
> Credits: 9,500
> Tier: Premium
>
> Available tools:
> - get_perspectives (query multiple AI models)
> - get_cli_status (check local CLI tools)
> - send_cli_prompt (use local CLIs)
>
> Dashboard: https://polydev.ai/dashboard

**If not authenticated**:
> Not authenticated.
>
> To login:
> 1. Use `/polydev-login` (opens browser)
> 2. Or run in terminal: `npx polydev-ai`
>
> After login, restart your IDE.

## Quick Links

- Dashboard: https://polydev.ai/dashboard
- Models: https://polydev.ai/dashboard/models
- Usage: https://polydev.ai/dashboard/usage
