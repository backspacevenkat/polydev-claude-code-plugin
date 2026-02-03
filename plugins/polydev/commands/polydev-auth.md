# /polydev-auth - Check Authentication Status

Check your Polydev authentication status and remaining credits.

## Instructions

When the user runs `/polydev-auth`:

1. **Check if POLYDEV_USER_TOKEN is set** by running:
   ```bash
   echo $POLYDEV_USER_TOKEN
   ```

2. **If token exists** (starts with `pd_`):
   - Confirm authentication is configured
   - Try using the polydev MCP tool to verify it works
   - Show remaining credits if available

3. **If token is missing or invalid**:
   - Guide them to run `/polydev-login`

## Response Template

### If authenticated:

---

## ✅ Polydev Authentication Status

**Status:** Authenticated
**Token:** `pd_****...****` (configured)

To check your credits and usage, visit:
👉 [polydev.ai/dashboard](https://polydev.ai/dashboard)

**Test it:** Ask me to "get polydev perspectives on [any coding question]"

---

### If NOT authenticated:

---

## ❌ Polydev Authentication Status

**Status:** Not configured

Your `POLYDEV_USER_TOKEN` environment variable is not set.

### Quick Setup:

1. **Get your free token:** [polydev.ai/dashboard/mcp-tokens](https://polydev.ai/dashboard/mcp-tokens)

2. **Add to your shell:**
   ```bash
   echo 'export POLYDEV_USER_TOKEN="pd_your_token"' >> ~/.zshrc
   source ~/.zshrc
   ```

3. **Restart Claude Code**

Or run `/polydev-login` for guided authentication.

---
