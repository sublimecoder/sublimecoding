# System Design — Idempotent Endpoint

A Claude Code / Cursor prompt for designing idempotent endpoints that survive real-world client retries — payments, webhooks, mutation APIs.

**Use when:** Designing any write endpoint that a client might retry — payments, webhooks, mutation APIs, anything that crosses a network you don't own.

**Why it works:** "Just add an idempotency key" is the answer that gets you 60% of the way there and silently leaks money in production. This prompt forces the design conversation past the easy part.

---

```
Design an idempotent version of this endpoint. Assume the caller will retry on any 5xx, network timeout, or unclear response — because they will.

Cover:
1. Idempotency key: who generates it (client vs. server), how long it's valid, where it's stored, and what happens on collision with a different request body.
2. The exact state machine for a single key: first request, in-flight retry, completed retry, failed retry. What does each return?
3. Storage: which table, which index, which TTL, and how this scales when the endpoint takes 1K req/s.
4. Failure modes I'm probably ignoring: partial writes, dual-region replication lag, key reuse across tenants, garbage collection of old keys.
5. The smallest test suite that proves the implementation is actually idempotent under retry, not just "looks idempotent in the happy path."

ENDPOINT:
<paste contract / handler here>
```

---

### Want the other 49?

This is one of 5 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents).

**$39 founders edition** (first 50 buyers, then $49) · 7-day refund · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

Other free samples: [code review](./code-review-blast-radius.md) · [debugging](./debugging-hypothesis-driven.md) · [refactoring](./refactoring-long-functions.md) · [PR descriptions](./docs-pr-description.md)
