# /polydev-login - Authenticate with Polydev

Authenticate with Polydev using browser-based OAuth. This provides a seamless login experience.

## Instructions

When the user runs `/polydev-login`, follow these steps:

1. **Open the CLI authentication page** in the user's browser:
   ```
   https://polydev.ai/auth/cli?redirect=claude-code
   ```

2. **Guide them through the process:**
   - New users: Sign up with Google or GitHub (free)
   - Existing users: Page shows their token automatically

3. **The page provides:**
   - One-click token copy
   - Ready-to-run shell command
   - Step-by-step instructions

## Response Template

Show this to the user:

---

## 🔐 Polydev Authentication

**👉 [Click here to authenticate](https://polydev.ai/auth/cli?redirect=claude-code)**

This opens a dedicated CLI authentication page that will:

1. **Sign you in** with Google or GitHub (if not logged in)
2. **Show your API token** with one-click copy
3. **Provide the exact command** to add to your shell

### After Getting Your Token

The page will give you a command like:
```bash
echo 'export POLYDEV_USER_TOKEN="pd_your_token"' >> ~/.zshrc && source ~/.zshrc
```

Then restart Claude Code and run `/mcp` to verify the connection.

---

### ✅ Already Authenticated?

Run `/polydev-auth` to check your current authentication status.

**Need help?** Run `/polydev-help` for troubleshooting tips.

---
