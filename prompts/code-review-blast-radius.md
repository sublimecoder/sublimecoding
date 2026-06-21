# Code Review — Blast Radius Analysis

A staff-level Code Review prompt for Claude Code, Cursor, and other AI coding assistants.

**Use it when:** Before merging a PR that touches shared infrastructure.

**Why it works:** Forces the model to reason about systems-level consequences instead of nitpicking syntax. The single-sentence verdict prevents the wishy-washy "it depends" output that wastes review time.

---

```
Act as a Staff engineer reviewing this diff for blast radius before merge.

For each changed file, answer:
1. What systems, services, or callers depend on this code path?
2. What's the worst realistic failure mode if this ships broken?
3. Is the change reversible without a backfill, replay, or schema rollback?
4. What monitoring would I check in the first 30 minutes after deploy?

End with a single sentence verdict: SAFE TO MERGE, MERGE WITH MITIGATION, or HOLD.
If MERGE WITH MITIGATION, list the mitigations in priority order.

Diff:
<paste diff or attach file>
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
