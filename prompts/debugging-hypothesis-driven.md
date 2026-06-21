# Debugging — Hypothesis-Driven Debugging

A staff-level Debugging prompt for Claude Code, Cursor, and other AI coding assistants.

**Use it when:** When you've been staring at a bug for 30 minutes and need a reset.

**Why it works:** Most debugging time is wasted on the first plausible explanation. Forcing 5 hypotheses + cheapest-falsification rebuilds the scientific method when fatigue has eroded it.

---

```
I'm debugging a problem. Reset me. Walk me through this rigorously.

Symptom (what I observe):
<describe>

What should happen:
<describe>

What I've already ruled out:
<list>

Now:
1. Generate 5 hypotheses ordered by likelihood given typical failure modes in this stack.
2. For each hypothesis, write the cheapest test that would falsify it.
3. Identify which test gives me the most information per minute spent.
4. If two hypotheses are entangled, propose the ordering that disentangles them fastest.

Don't suggest fixes yet. We're isolating, not fixing.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
