# CLAUDE.md Starter — Elixir / Phoenix

A drop-in `CLAUDE.md` for Elixir codebases — Phoenix apps, umbrella projects, OTP services — so [Claude Code](https://claude.com/claude-code) stops writing Ruby in Elixir syntax and actually respects your supervision tree, contexts, and let-it-crash conventions.

By [Jared Smith](https://sublimecoding.com) — staff engineer, Director of Information Security at Lavender. Production Elixir at AAMP Global (40K+ telematics devices streaming). 13+ years shipping Go, Elixir, and Ruby.

## What this is

A real, opinionated `CLAUDE.md` that:

- Tells Claude Code your umbrella layout, context boundaries, and OTP supervision shape
- Sets the rules for GenServers, processes, and where state actually belongs
- Locks in the Ecto changeset / context / schema separation
- Lists the anti-patterns (Rails-isms, premature actor model, `try`/`rescue` overuse) you don't want suggested
- Gives Claude the mix tasks so it stops inventing them

This file goes at the root of your repo. Claude Code reads it on every run and uses it to ground its suggestions.

## Quick start

1. Copy [`CLAUDE.md`](./CLAUDE.md) into the root of your Elixir project.
2. Fill in the `[bracketed]` fields — app name, Phoenix vs not, umbrella vs single-app, primary database, deployment target.
3. Delete sections that don't apply. Add ones that do.
4. Commit it. Claude Code now starts every session with your conventions in context.

## Why CLAUDE.md matters more in Elixir

Elixir is the language Claude Code hallucinates hardest on. It has less training data than Go or Python, and the model frequently confuses Elixir with Ruby or Erlang. Without conventions in context, you get:

- GenServers used where a plain function would do
- `try`/`rescue` blocks that should be pattern matches
- Mutated state that doesn't exist
- "Service objects" that should be contexts

A `CLAUDE.md` cuts most of this on the first message.

## What's in the Vault

This is the **Elixir-only** starter. The [Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault) includes:

- 3 `CLAUDE.md` starters: **Go services**, **Elixir umbrellas**, **AI agent projects**
- 5 `.cursorrules` files (one per category — code review, debugging, refactoring, system design, docs)
- 50 production-tested prompts for Claude Code and Cursor
- Notion blueprint with category, tool, and usage views

**$39 founders edition** — first 50 buyers, then $49 · 7-day refund · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

## Related

- [Go CLAUDE.md starter](https://github.com/sublimecoder/claude-md-go-starter)
- [5 free sample prompts](https://github.com/sublimecoder/sublimecoding/tree/main/prompts)
- [How I Prompt Claude as a Staff Engineer (50 Prompts I Actually Use)](https://sublimecoding.com/blog/staff-engineer-claude-prompts)
- [sublimecoding.com](https://sublimecoding.com)

## License

MIT. Use it, fork it, ship it.
