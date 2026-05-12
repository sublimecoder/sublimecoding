# Refactoring — Long Functions

A Claude Code / Cursor prompt for refactoring long functions without breaking load-bearing side effects or widening the public surface.

**Use when:** A function has grown past comprehension but the surrounding tests are weak. Lets you extract without losing intent or quietly breaking a load-bearing side effect.

**Why it works:** Most "AI refactoring" goes wrong by extracting along line boundaries instead of intent boundaries, or by silently rearranging side effects that look accidental but aren't. This prompt makes both failure modes explicit.

---

```
This function is too long but I don't fully trust the surrounding tests. Refactor it without changing behavior.

Rules:
1. Don't introduce new dependencies, frameworks, or design patterns. Use the language and conventions already in this file.
2. Extract by intent, not by line count. Each extracted function gets a name that describes what it does for the caller, not how it does it.
3. Preserve every side effect, including order, even ones that look accidental — they may be load-bearing. Flag any side effect you suspect is a bug, but don't silently change it.
4. Don't widen any return type, error path, or argument shape. Public surface stays identical.
5. After the refactor, list every behavior I should write a characterization test for before I merge.

FUNCTION:
<paste here>
```

---

### Want the other 49?

This is one of 5 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents).

**$39 founders edition** (first 50 buyers, then $49) · 7-day refund · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

Other free samples: [code review](./code-review-blast-radius.md) · [debugging](./debugging-hypothesis-driven.md) · [system design](./system-design-idempotency.md) · [PR descriptions](./docs-pr-description.md)
