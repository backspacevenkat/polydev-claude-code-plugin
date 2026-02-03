# /polydev-login - Browser-based Authentication

Authenticate with Polydev using browser-based OAuth. This provides a seamless login experience.

## Instructions

When the user runs `/polydev-login`, follow these steps:

1. **Open the authentication URL** in the user's browser:
   ```
   https://polydev.ai/auth/cli?redirect=claude-code
   ```

2. **Tell the user** to complete authentication in their browser (Google or GitHub OAuth)

3. **After authentication**, the user will see their token on the page. Instruct them to:
   - Copy the token (starts with `pd_`)
   - Add it to their shell profile:
     ```bash
     echo 'export POLYDEV_USER_TOKEN="pd_their_token"' >> ~/.zshrc
     source ~/.zshrc
     ```

4. **Restart Claude Code** to pick up the new environment variable

## Response Template

Show this to the user:

---

## 🔐 Polydev Authentication

Opening your browser for authentication...

**👉 [Click here to authenticate](https://polydev.ai/auth/cli?redirect=claude-code)**

### After logging in:

1. Copy your token from the page (starts with `pd_`)
2. Run this command in your terminal:
   ```bash
   echo 'export POLYDEV_USER_TOKEN="pd_YOUR_TOKEN_HERE"' >> ~/.zshrc && source ~/.zshrc
   ```
3. Restart Claude Code
4. Run `/mcp` to verify connection

**Need help?** Run `/polydev-help` for troubleshooting tips.

---
