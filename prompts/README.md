## Sample prompts from The Senior Engineer's AI Prompt Vault

Five prompts pulled from the [Vault](https://sublimecoding.com/vault) — one from each of the five categories. They run as-is in Claude Code, Cursor, or any coding assistant that takes a system prompt or chat message.

Each one encodes how I actually use AI as a staff engineer: forcing structured thinking instead of pattern-matched answers, naming the failure modes I care about, and making the model commit to a recommendation instead of hedging.

### What's here

| Category | Prompt |
|---|---|
| Code Review | [Blast Radius](./code-review-blast-radius.md) |
| Debugging | [Hypothesis-Driven Root Cause](./debugging-hypothesis-driven.md) |
| Refactoring | [Long Functions](./refactoring-long-functions.md) |
| System Design | [Idempotent Endpoint](./system-design-idempotency.md) |
| Docs & PRs | [High-Signal PR Description](./docs-pr-description.md) |

### What's in the full Vault

- 50 prompts (10 per category)
- 5 `.cursorrules` files (one per category)
- 3 `CLAUDE.md` starters: Go services, Elixir umbrellas, AI agent projects
- Notion blueprint with category, tool, and usage views
- Lifetime updates · 7-day refund

**$39 founders edition** — first 50 buyers, then $49.

→ **[Get the Vault](https://sublimecoding.com/vault)**

---

### How to use these

Drop the prompt into your chat or system prompt. Replace the `<paste here>` marker with the diff, function, endpoint, or context. Most are tuned to refuse hedging — if the model gives you a wishy-washy answer, paste the prompt again with "Pick one and commit." appended.

These prompts assume you've done the basics: written the failing test, run the linter, read the error twice. They're for the part where the work is actually hard.
