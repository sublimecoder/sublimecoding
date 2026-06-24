# Claude Code Migration Safety Review Prompt

A staff-level database migration safety review prompt for Claude Code, Cursor, and other AI coding assistants — for any DDL change against a live, large production database.

**Use it when:** Reviewing any DDL change against a live, large production database.

**Why it works:** DDL is where ORMs lie to engineers about safety. This prompt forces the model to reason about lock semantics and online migration patterns.

---

```
Review this database migration as a Staff engineer who's been paged at 3am for a long-running ALTER.

Assume the table has at least 50 million rows and the database is under live write load.

For each statement, answer:
1. Does it acquire a lock that blocks reads or writes? Which lock and for how long?
2. Does it require a full table rewrite? (estimate runtime)
3. Is there a non-blocking equivalent? (e.g. CONCURRENTLY, online schema change, expand-then-contract)
4. Is it reversible? Is there a down migration?
5. Is it safe to run while application code is mid-deploy? (i.e. compatible with both old and new app versions)

End with: SAFE / NEEDS REWRITE, and the safer plan if NEEDS REWRITE.

Migration:
<paste>
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
