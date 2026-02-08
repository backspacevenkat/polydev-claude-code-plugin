---
description: One-click browser authentication for Polydev
---

# /polydev-login - Browser Authentication

Login to Polydev directly from your IDE or sandboxed environment.

## Instructions

When the user runs `/polydev-login`:

### Step 1: Check if MCP tools are available

Look for tools starting with `mcp__plugin_polydev_mcp__` in your available tools list.

### Step 2a: If MCP tools ARE available

Call the `login` tool:
```
mcp__plugin_polydev_mcp__login({ open_browser: true })
```

If browser login fails or the environment is sandboxed, the user can pass their token directly:
```
mcp__plugin_polydev_mcp__login({ user_token: "pd_user_token_here" })
```
Get the token from https://polydev.ai/dashboard

### Step 2b: If MCP tools are NOT available (Cowork / sandboxed environments)

Use this bash-based login flow instead:

```bash
# Generate a unique session ID
SESSION_ID=$(openssl rand -hex 32)

# Create the login session on the server
curl -s -X POST "https://www.polydev.ai/api/auth/cli-session/${SESSION_ID}" \
  -H "Content-Type: application/json"

# Generate the auth URL
echo ""
echo "========================================="
echo "  Open this URL in your browser to login:"
echo "========================================="
echo ""
echo "https://polydev.ai/auth?session_id=${SESSION_ID}&redirect=ide-plugin&auto=true"
echo ""
echo "Waiting for authentication..."
```

Show the auth URL to the user and ask them to open it in their browser.

Then poll for the token:

```bash
# Poll every 3 seconds for up to 5 minutes
for i in $(seq 1 100); do
  RESULT=$(curl -s "https://www.polydev.ai/api/auth/cli-session/${SESSION_ID}")
  STATUS=$(echo "$RESULT" | python3 -c "import sys,json; d=json.load(sys.stdin); print(d.get('status',''))" 2>/dev/null)

  if [ "$STATUS" = "completed" ]; then
    TOKEN=$(echo "$RESULT" | python3 -c "import sys,json; print(json.load(sys.stdin).get('token',''))" 2>/dev/null)
    if [ -n "$TOKEN" ]; then
      # Save token to config files
      mkdir -p ~/.config/polydev
      echo "POLYDEV_USER_TOKEN=${TOKEN}" > ~/.polydev.env

      # Add to shell config if not already present
      if ! grep -q "POLYDEV_USER_TOKEN" ~/.zshrc 2>/dev/null && ! grep -q "POLYDEV_USER_TOKEN" ~/.bashrc 2>/dev/null; then
        SHELL_RC="$HOME/.bashrc"
        [ -f "$HOME/.zshrc" ] && SHELL_RC="$HOME/.zshrc"
        echo "" >> "$SHELL_RC"
        echo "# Polydev AI token" >> "$SHELL_RC"
        echo "export POLYDEV_USER_TOKEN=\"${TOKEN}\"" >> "$SHELL_RC"
      fi

      echo ""
      echo "Login successful! Token saved."
      echo "Please restart your IDE for the token to take effect."
      break
    fi
  fi

  if [ "$STATUS" = "expired" ] || [ "$STATUS" = "not_found" ]; then
    echo "Session expired or not found. Please try again."
    break
  fi

  sleep 3
done
```

### Step 3: After success

Tell the user:
- Token has been saved to `~/.polydev.env` and their shell config
- They need to **restart their IDE** for the token to take effect
- After restart, they can use `/polydev:ask` to query multiple AI models

## Example

**User**: `/polydev-login`

**If MCP tools available**: Call the login MCP tool directly.

**If in Cowork/sandbox**: Run the bash commands above, show the auth URL, wait for completion.

**On success**:
> Login successful! Your token has been saved.
>
> **Important:** Restart your IDE to activate the token.
>
> After restart, use `/polydev:ask` to query multiple AI models.

## Troubleshooting

- If in a sandboxed VM with no browser, copy the auth URL and open it on your local machine
- Check internet connectivity with: `curl -s https://www.polydev.ai/api/health`
- If all else fails, visit https://polydev.ai/auth directly, copy your token, and add `export POLYDEV_USER_TOKEN="your_token"` to your shell config
