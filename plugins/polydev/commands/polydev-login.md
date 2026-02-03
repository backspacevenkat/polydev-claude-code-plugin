# /polydev-login - Get Your Polydev Token

Guide users through getting and configuring their Polydev API token.

## Instructions

When the user runs `/polydev-login`, follow these steps:

1. **Open the Connect IDE page** in the user's browser:
   ```
   https://polydev.ai/dashboard/mcp-tokens
   ```

2. **Guide them through the page:**
   - If not logged in: Sign up/login with Google or GitHub
   - If logged in: The page shows their tokens and setup instructions

3. **Help them configure the token:**
   - Copy their token (starts with `pd_`)
   - Add to shell profile
   - Restart Claude Code

## Response Template

Show this to the user:

---

## 🔐 Polydev Setup

### Step 1: Get Your Token

**👉 [Open Polydev Dashboard](https://polydev.ai/dashboard/mcp-tokens)**

- **New user?** Sign up free with Google or GitHub
- **Existing user?** Your tokens are listed on this page

### Step 2: Copy Your Token

On the dashboard, find "Your API Tokens" section and copy your token (starts with `pd_`).

If you don't have one, click **"+ Create Token"**.

### Step 3: Add to Your Shell

Run this in your terminal (replace with your actual token):

```bash
echo 'export POLYDEV_USER_TOKEN="pd_YOUR_TOKEN_HERE"' >> ~/.zshrc
source ~/.zshrc
```

### Step 4: Restart Claude Code

Close and reopen Claude Code, then run `/mcp` to verify "polydev" appears.

---

### ✅ Quick Test

After setup, try: "Get polydev perspectives on best practices for error handling"

**Need help?** Run `/polydev-help` for troubleshooting.

---
