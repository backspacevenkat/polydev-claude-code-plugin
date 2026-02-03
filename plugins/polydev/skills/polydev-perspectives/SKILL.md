---
name: polydev-perspectives
description: Get multi-model AI perspectives on any coding question. Use when user is stuck, needs code review, architecture advice, or debugging help.
version: 1.0.0
allowed-tools:
- Bash(general:*)
- Read
- Grep
- Glob
license: MIT
---
# Polydev Perspectives

## Overview

Get instant perspectives from multiple AI models (GPT-4, Claude, Gemini, Grok) on any coding question. Perfect for debugging, architecture decisions, and code reviews.

## Usage

Run `/polydev-perspectives` followed by your question.

Example:
```
/polydev-perspectives How should I structure my React authentication flow?
```

## When to Use

- **Debugging**: When stuck on a bug and need fresh perspectives
- **Architecture**: When making design decisions
- **Code Review**: When you want multiple viewpoints on your code
- **Best Practices**: When learning optimal approaches

## How It Works

1. Your question is sent to multiple AI models simultaneously
2. Each model provides its unique perspective
3. Results are aggregated and presented for comparison
4. You get diverse viewpoints to make better decisions

## Prerequisites

- Must be authenticated with Polydev (`/polydev-login`)
- Active internet connection
- Sufficient credits in your Polydev account

## Example Questions

- "What's the best way to handle errors in async JavaScript?"
- "Review this function for potential bugs: [paste code]"
- "Should I use Redux or Context for state management?"
- "How do I optimize this database query?"
