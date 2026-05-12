# Debugging — Hypothesis-Driven Root Cause

A Claude Code / Cursor prompt that stops AI from pattern-matching a fix before the actual root cause is identified.

**Use when:** A bug is reproducible but the cause isn't obvious. Stops the model from pattern-matching to a plausible-looking fix that doesn't actually address the cause.

**Why it works:** The default failure mode for AI debugging is generating a fix that "looks like it should work" before the cause is even identified. This prompt makes the model show its work and earn the fix.

---

```
A bug is reproducible. I want a root cause, not a fix.

Before suggesting any code change, do this:

1. State three competing hypotheses for what's actually broken. Rank them by likelihood given only the evidence I've given you. Do not collapse to one until we have evidence that rules the others out.
2. For each hypothesis, name the single cheapest experiment, log line, or query that would falsify it.
3. Tell me what evidence I'd need to see to be 95% sure of the cause. If the evidence I've given you isn't enough, say what's missing.
4. Once we have a cause, only then propose a fix. The fix must include a regression test that fails before the fix and passes after.

Symptoms, repro steps, and what I've tried already:
<paste here>
```

---

### Want the other 49?

This is one of 5 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents).

**$39 founders edition** (first 50 buyers, then $49) · 7-day refund · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

Other free samples: [code review](./code-review-blast-radius.md) · [refactoring](./refactoring-long-functions.md) · [system design](./system-design-idempotency.md) · [PR descriptions](./docs-pr-description.md)
