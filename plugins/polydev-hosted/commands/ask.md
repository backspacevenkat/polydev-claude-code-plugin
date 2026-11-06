---
description: Ask several other AI models the same question and compare their answers
argument-hint: Your question or problem
---

# /polydev-hosted:ask [question]

Ask the other AI models set up in the user's Polydev account the same question, then compare the answers.

1. Take the question from the argument; if there is none, use the problem being discussed.
2. Add only the context the models need (relevant code, the error, constraints). Leave out secrets, keys and
   unrelated files: Polydev passes the prompt to other model providers.
3. Call the `get_perspectives` tool of the `polydev` MCP server with that prompt. The first call asks the user
   to sign in to Polydev in the browser.
4. Summarise where the models agree, where they differ, and what you recommend.
