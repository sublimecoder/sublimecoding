# Debugging — Reproduce a Race Condition Reliably

A staff-level Debugging prompt for Claude Code, Cursor, and other AI coding assistants.

**Use it when:** When the bug appears once a week in production but never on your laptop.

**Why it works:** The hardest part of race debugging is reliable repro. Forcing the model to write the test before the fix prevents the "I think this is fine now" cycle that ships unverified patches.

---

```
I have a suspected race condition that won't reproduce locally. Help me force it.

The code:
<paste>

What I think races:
<describe>

Generate:
1. A minimal test that exercises the race, using sleeps, sync.WaitGroups, or runtime.Gosched calls (Go) / equivalents in my language.
2. The exact interleaving I need to force.
3. How to use the race detector (`-race` in Go, ThreadSanitizer in C/C++, jstack/yourkit in JVM, etc).
4. If the race is timing-dependent, a stress test (e.g. 1000 iterations) wrapped around it.
5. Whether changing CPU pinning, GOMAXPROCS, or scheduler tunables would help.

Write the test now. Don't propose the fix yet.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
