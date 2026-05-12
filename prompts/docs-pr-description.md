# Docs & PRs — High-Signal PR Description

A Claude Code / Cursor prompt for writing PR descriptions a busy reviewer will actually read — structured around what they care about, not the diff.

**Use when:** You're about to open a PR and don't want to write "this PR does X" three times. Also useful for retroactively documenting a messy branch.

**Why it works:** Most generated PR descriptions narrate the diff. A good one helps the reviewer decide what to actually look at. This prompt is structured around what reviewers care about, not what's easy to summarize.

---

```
Write a PR description from this diff. The audience is a reviewer who is busy and will not read the diff line-by-line until your description earns it.

Structure:
- One-sentence summary at the top. Lead with the user-visible outcome or system change, not the file you touched.
- "Why now": the trigger — bug ID, incident, customer ask, deadline. If you don't know, ask me.
- "What changed": 3–6 bullets, grouped by surface (API / DB / worker / UI / config). Skip files that are pure refactors of touched code.
- "What didn't change": call out the boring guarantees explicitly — public API stable, no migration required, no config change. This is what the reviewer is actually checking for.
- "How I tested": commands run, environments hit, edge cases verified. If something wasn't tested, say so.
- "Rollback plan": one line.

No emoji. No "this PR aims to". Active voice. If a section is empty, omit it instead of writing "N/A".

DIFF + context:
<paste here>
```

---

### Want the other 49?

This is one of 5 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents).

**$39 founders edition** (first 50 buyers, then $49) · 7-day refund · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

Other free samples: [code review](./code-review-blast-radius.md) · [debugging](./debugging-hypothesis-driven.md) · [refactoring](./refactoring-long-functions.md) · [system design](./system-design-idempotency.md)
