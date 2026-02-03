---
name: polydev-login
description: Login to Polydev and save your API token. Use when user needs to authenticate with Polydev or set up their token.
version: 1.0.0
allowed-tools:
- Bash(general:*)
license: MIT
---
# Polydev Login

## Overview

This skill helps users authenticate with Polydev to get their API token for multi-model AI consultations.

## Usage

Run `/polydev-login` to start the authentication flow.

## Workflow

1. **Check CLI Installation**: First verify if `polydev-ai` CLI is installed:
   ```bash
   which polydev-login || echo "CLI not installed"
   ```

2. **Install CLI if needed**: If not installed, prompt user to install:
   ```bash
   npm install -g polydev-ai
   ```

3. **Run Login**: Execute the login command which opens browser for OAuth:
   ```bash
   polydev-login
   ```

4. **Verify**: After login, verify the token was saved:
   ```bash
   polydev-login status
   ```

## What Happens

1. Opens browser to `polydev.ai/auth/cli` with callback URL
2. User authenticates via Google or GitHub OAuth
3. Token is automatically saved to `~/.zshrc` and `~/.polydev.env`
4. Browser shows Polydev-branded success page
5. User can close browser and start using Polydev

## Troubleshooting

- If browser doesn't open, manually visit the URL shown in terminal
- If token not saved, check write permissions for `~/.zshrc`
- Run `source ~/.zshrc` to load token in current shell
