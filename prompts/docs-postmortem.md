# Claude Code Postmortem Prompt

A staff-level incident postmortem prompt for Claude Code, Cursor, and other AI coding assistants — draft the postmortem the day after, while context is fresh.

**Use it when:** Writing the postmortem the day after, while context is fresh.

**Why it works:** Postmortems often slip into blame or PR-speak. The structure + voice rules produce documents the team will actually read and the legal team won't redact.

---

```
Draft a blameless postmortem from these incident notes.

Notes:
<paste timeline + investigation summary>

Use this structure:

# Postmortem: <one-line summary>

## Summary
What happened, in two sentences.

## Impact
Quantified. Users affected, duration, money or trust lost.

## Timeline
UTC. Each entry: time | event.

## Root cause
What actually caused it. Not "human error." A specific failure of code, process, or infrastructure.

## Contributing factors
The conditions that allowed the root cause to escape detection or amplify.

## What went well
Something. There's always something.

## What went poorly
Honest assessment. No blame, just facts.

## Action items
Each: owner, ticket, due date. Specific and finishable.

Voice: matter-of-fact, blameless. Never name individuals as causes.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
