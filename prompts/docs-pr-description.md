# Claude Code PR Description Prompt

A staff-level PR description prompt for Claude Code, Cursor, and other AI coding assistants — generate a reviewable PR description from your diff.

**Use it when:** Same as code-review-10, used for self-authoring not review.

**Why it works:** A consistent template authored to a clear voice gets PRs reviewed faster. Devs stop rewriting their own descriptions every time.

---

```
Read this diff and write the PR description from the author's perspective.

Use:
**What**. one paragraph, plain English.
**Why**. link or write the reason. Don't apologize.
**How to verify**. steps a reviewer can run.
**Risk + rollback**. blast radius, failure modes, the rollback.
**Out of scope**. what this PR does not do.

Voice: declarative, factual. No "tiny cleanup" minimizing. No "should fix the issue we discussed" hedging.

Diff:
<paste>
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_body&utm_campaign=vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_footer&utm_campaign=vault)**  ·  **[Consulting for production AI & scale](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompt_footer&utm_campaign=consulting)**  ·  **[← all 15 sample prompts](./README.md)**
