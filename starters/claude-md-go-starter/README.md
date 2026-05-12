# CLAUDE.md Starter — Go Services

A drop-in `CLAUDE.md` for Go service codebases — APIs, workers, microservices — so [Claude Code](https://claude.com/claude-code) actually understands your conventions on the first message instead of pattern-matching to whatever it saw on GitHub.

By [Jared Smith](https://sublimecoding.com) — staff engineer, Director of Information Security at Lavender, 13+ years shipping production Go, Elixir, and Ruby. 100K+ users on live AI products. $400M+ in fintech assets protected.

## What this is

A real, opinionated `CLAUDE.md` that:

- Tells Claude Code your project structure, error-handling shape, logging shape, and testing rules
- Lists the anti-patterns you don't want it to suggest
- Gives it the common commands (build, test, lint, migrate) so it stops guessing
- Sets the bar for what "done" means in your codebase

This file goes at the root of your repo. Claude Code reads it on every run and uses it to ground its suggestions.

## Quick start

1. Copy [`CLAUDE.md`](./CLAUDE.md) into the root of your Go project.
2. Fill in the `[bracketed]` fields — service name, primary database, deployment target, etc.
3. Delete sections that don't apply. Add ones that do.
4. Commit it. Claude Code now starts every session with your conventions in context.

## Why CLAUDE.md matters

Without one, Claude Code guesses your conventions from the files it reads. That's fine for greenfield repos and disastrous for older codebases with a specific style. The bigger the codebase, the more it pattern-matches to the *wrong* parts of it.

A good `CLAUDE.md` is a 5-minute investment that fixes 80% of "the model keeps doing X and I keep correcting it" frustrations.

## What's in the Vault

This is the **Go-only** starter. The [Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault) includes:

- 3 `CLAUDE.md` starters: **Go services**, **Elixir umbrellas**, **AI agent projects**
- 5 `.cursorrules` files (one per category — code review, debugging, refactoring, system design, docs)
- 50 production-tested prompts for Claude Code and Cursor
- Notion blueprint with category, tool, and usage views

**$39 founders edition** — first 50 buyers, then $49 · 7-day refund · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

## Related

- [5 free sample prompts](https://github.com/sublimecoder/sublimecoding/tree/main/prompts)
- [How I Prompt Claude as a Staff Engineer (50 Prompts I Actually Use)](https://sublimecoding.com/blog/staff-engineer-claude-prompts)
- [The Claude Code Resource Bible: 46 Tools Worth Knowing in 2026](https://sublimecoding.com/blog/claude-code-resource-bible)
- [sublimecoding.com](https://sublimecoding.com)

## License

MIT. Use it, fork it, ship it.
