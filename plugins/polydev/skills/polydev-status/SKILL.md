---
name: polydev-status
description: Check Polydev authentication status and CLI installation. Use when user wants to verify their Polydev setup.
version: 1.0.0
allowed-tools:
- Bash(general:*)
license: MIT
---
# Polydev Status

## Overview

This skill checks the current Polydev setup including CLI installation and authentication status.

## Usage

Run `/polydev-status` to check your setup.

## Checks Performed

1. **CLI Installation**: Verify polydev-ai CLI is installed
   ```bash
   which polydev-login && polydev-login --version
   ```

2. **Authentication Status**: Check if user is authenticated
   ```bash
   polydev-login status
   ```

3. **Token Location**: Verify token is in shell config
   ```bash
   grep POLYDEV_USER_TOKEN ~/.zshrc
   cat ~/.polydev.env
   ```

## Expected Output

When properly configured:
```
✓ Authenticated with Polydev
  Token: pd_xxxxx...xxxxx
```

When not authenticated:
```
✗ Not authenticated
  Run 'polydev-login' to authenticate
```
