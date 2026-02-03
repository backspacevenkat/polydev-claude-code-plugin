---
description: One-click browser authentication for Polydev
---

# /polydev-login - Browser Authentication

Login to Polydev directly from your IDE. Opens browser for one-click authentication.

## Instructions

When the user runs `/polydev-login`:

1. **Call the login MCP tool**:
   ```
   Use the polydev MCP server's "login" tool
   ```

2. **The tool will**:
   - Open the browser to polydev.ai/auth/cli
   - Wait for user to authenticate (Google/GitHub)
   - Auto-save token to ~/.zshrc and ~/.polydev.env
   - Return success message

3. **After success**, remind user to restart their IDE.

## Example

**User**: `/polydev-login`

**Claude uses the login tool from polydev MCP server**

**On success**:
> Login successful!
>
> Your token has been saved automatically.
>
> **Important:** Restart your IDE to use the new token.
>
> After restart, use `/polydev` or `get_perspectives` to query multiple AI models.

## Alternative

If the MCP tool doesn't work, users can run in terminal:
```bash
npx polydev-ai
```

## Troubleshooting

- Ensure browser is available
- Check internet connection
- If browser doesn't open, visit: https://polydev.ai/auth/cli
