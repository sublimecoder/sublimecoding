# Claude Code Idempotency Design Prompt

A staff-level idempotency design prompt for Claude Code, Cursor, and other AI coding assistants — for any API that mutates state and might be retried.

**Use it when:** Any API that mutates state and might be retried (i.e. all of them).

**Why it works:** Idempotency is a category, not a feature. Walking through retry scenarios + strategy fit + concurrency catches the "I added a unique constraint and called it a day" mistake.

---

```
Design idempotency for this operation.

Operation:
<describe>

Walk through:
1. The retry scenarios that produce duplicates (network, timeout, client retry, queue redelivery).
2. The idempotency strategy options:
   - Idempotency key (header), server caches result by key
   - Natural key (e.g. order_id from client)
   - Optimistic locking (version)
   - Conditional writes (compare-and-set)
3. The right strategy for THIS operation, with reasoning.
4. Storage: where the idempotency record lives, TTL, what's stored (full response? hash?).
5. Concurrency: what happens if two retries arrive at the same time?
6. The contract: what HTTP status do we return on a replay (200 same body? 409? 304?).
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_body&utm_campaign=vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_footer&utm_campaign=vault)**  ·  **[Consulting for production AI & scale](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompt_footer&utm_campaign=consulting)**  ·  **[← all 15 sample prompts](./README.md)**
