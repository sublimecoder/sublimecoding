# Claude Code God Class Refactoring Prompt

A staff-level god class refactoring prompt for Claude Code, Cursor, and other AI coding assistants — untangle a 1500-line service that does everything.

**Use it when:** 1500-line UserService that does everything.

**Why it works:** God classes are decomposed in PRs, not in one rewrite. The facade pattern lets you ship the first split with zero blast radius and prove the seam before going further.

---

```
This class does too much. Help me decompose it without breaking callers.

Class:
<paste>

Do this:
1. List every responsibility you see. (Don't merge them yet.)
2. Group responsibilities by what data they touch and what they collaborate with.
3. Propose 3-5 smaller types, each with a single reason to change.
4. Define the original class as a thin facade that delegates to the new types, so callers don't break.
5. Show me the migration order: which extraction is safest to do first.

Constraint: zero behavioral change, zero call site changes in the first PR.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_body&utm_campaign=vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_footer&utm_campaign=vault)**  ·  **[Consulting for production AI & scale](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompt_footer&utm_campaign=consulting)**  ·  **[← all 15 sample prompts](./README.md)**
