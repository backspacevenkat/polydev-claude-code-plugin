---
description: Ask another AI model (or several) through Polydev
argument-hint: Your question, optionally naming a model (for example gpt-6.1-sol)
---

# /polydev-hosted:ask [question]

Send the user's question to another AI model through Polydev and show the answer.

1. Take the question from the argument; if there is none, use the problem being discussed.
2. If the user names a model (for example "gpt-6.1-sol" or "ask Gemini"), ask that model. If they name
   several, ask those. If they name none, ask their default set. `list_models` shows which models the
   account can reach.
3. Add only the context the model needs (relevant code, the error, constraints). Leave out secrets, keys and
   unrelated files: Polydev passes the prompt to other model providers.
4. Call the `ask_model` tool of the `polydev` MCP server with the prompt, plus `model` (one name) or
   `models` (a list) when the user named any. The first call asks the user to sign in to Polydev in the
   browser.
5. Show each answer with its "Paid by" line. If several models answered, say where they agree and differ,
   then what you recommend.
