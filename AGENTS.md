# AGENTS.md — Starter Template for Senior Engineers

> A production-grade `AGENTS.md` starter. `AGENTS.md` is the tool-agnostic instructions file read by
> Codex, Cursor, and other coding agents (the same content also works as `CLAUDE.md`).
> Free, from [The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=agents_md&utm_campaign=vault).
> Replace every `<…>` with your project's specifics, then delete this blockquote.

## Project
<One or two sentences: what this service does and who depends on it.>

## Stack
- Language: <e.g. Go 1.22 / Elixir 1.16>
- Framework: <e.g. Phoenix / chi>
- Data: <e.g. Postgres 16, Redis>
- Infra: <e.g. AWS ECS, Terraform>

## How to run
- Install: `<command>`
- Test: `<command>`
- Lint: `<command>`
- Dev server: `<command>`

## Conventions the agent MUST follow
- Read existing code and tests before changing anything. Match the established style.
- Do exactly what's asked — no unrequested abstractions, config, or drive-by refactors.
- Every changed line must trace to the task. Remove orphaned imports/vars; don't touch unrelated dead code.
- Handle the error path, not just the happy path. Make failures observable.
- For state-mutating, retryable operations, make them idempotent.

## Verification (required before claiming done)
- Run `<test command>` and confirm it passes.
- Run `<lint command>` and confirm it's clean.
- Report evidence (command + output), not assertions.

## Boundaries
- Never commit secrets. `.env` is git-ignored — do not stage it.
- Ask before deleting or renaming files outside `<src dir>`.
- Database migrations: <who reviews, how they run>.

## Where things live
- `<src/>` — <responsibility>
- `<test/>` — <responsibility>
- `<config/>` — <responsibility>

---

**Want the Go, Elixir & AI-agent `CLAUDE.md` starters too?** → [Free Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=agents_md&utm_campaign=vault)  ·  [Consulting](https://sublimecoding.com/consulting?utm_source=github&utm_medium=agents_md&utm_campaign=consulting)
