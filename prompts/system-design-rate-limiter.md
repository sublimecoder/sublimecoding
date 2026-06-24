# Claude Code Rate Limiter Design Prompt

A staff-level rate limiter design prompt for Claude Code, Cursor, and other AI coding assistants — adding rate limits to a public or partner API.

**Use it when:** Adding rate limits to a public or partner API.

**Why it works:** Rate limiter design is full of subtle choices that the casual answer ("use Redis") skips. The fail-open/closed and clock-skew prompts catch the gotchas.

---

```
Design a rate limiter for this scenario.

Scope:
- What's being limited? (per IP, per API key, per user, per route)
- Limits: <e.g. 100 req/min, 10K/day, burst 20>
- Distributed (multiple app servers) or single-node?

Pick from:
- Token bucket
- Leaky bucket
- Fixed window
- Sliding window log
- Sliding window counter

For your choice:
1. Why this algorithm for this scenario.
2. Storage backend (Redis Lua script, in-memory + sync, sidecar).
3. Failure mode: what happens if the rate limiter is down? Fail open or fail closed?
4. The response when limited: status code (429), headers (Retry-After, X-RateLimit-*), body.
5. How a client should back off (exponential? respect Retry-After?).
6. Edge cases: clock skew, key cardinality, hot keys.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_body&utm_campaign=vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_footer&utm_campaign=vault)**  ·  **[Consulting for production AI & scale](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompt_footer&utm_campaign=consulting)**  ·  **[← all 15 sample prompts](./README.md)**
