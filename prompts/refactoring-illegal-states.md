# Refactoring — Make Illegal States Unrepresentable

A staff-level Refactoring prompt for Claude Code, Cursor, and other AI coding assistants.

**Use it when:** When a struct has 4 optional fields and only some combos are valid.

**Why it works:** "Make illegal states unrepresentable" is the single highest-leverage refactor in static-typed code. The model knows the patterns by language and the prompt forces enumeration.

---

```
This data model allows states that should never exist. Help me redesign so the type system rejects them.

Type:
<paste>

Do this:
1. Enumerate the legal states (combinations of fields).
2. Enumerate the illegal states the current shape allows.
3. Propose a redesign, usually a sum type / discriminated union / tagged enum, that makes illegal states unrepresentable.
4. Show how callers change. Some will get simpler (no nil checks). Some will need to pattern match.

Language: <Go / Rust / TypeScript / Elixir / Ruby>
Pick the idiomatic encoding for that language.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
