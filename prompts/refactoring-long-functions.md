# Claude Code Refactoring Prompt — Decompose a Long Function

A staff-level long-function refactoring prompt for Claude Code, Cursor, and other AI coding assistants — decompose a 200-line function that does sequential things.

**Use it when:** 200-line function that does sequential things.

**Why it works:** "Extract until short" is how you get 50 anemic helpers. Extracting by reason produces functions that match how a reader thinks.

---

```
Decompose this function. Apply these principles in order:

1. Extract by REASON (sections that exist for a single reason), not by length.
2. Each extracted function gets a name describing the WHY, not the HOW.
3. Pass minimal arguments. If three calls in a row need the same five values, group them into a struct.
4. Keep extracted functions at the same level of abstraction as their caller.
5. Don't extract one-line helpers (they hurt more than they help).

Show me the original function as a sequence of 5-10 cleanly-named function calls.

Function:
<paste>
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_body&utm_campaign=vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_footer&utm_campaign=vault)**  ·  **[Consulting for production AI & scale](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompt_footer&utm_campaign=consulting)**  ·  **[← all 15 sample prompts](./README.md)**
