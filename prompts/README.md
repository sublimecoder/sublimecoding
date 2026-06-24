# Free Claude Code & Cursor Prompts for Senior Engineers

15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompts_index&utm_campaign=vault)** — production-tested prompts for Claude Code, Cursor, and other AI coding assistants. Each one encodes how a staff engineer actually uses AI: forcing structured thinking over pattern-matched answers, naming the failure modes that matter, and making the model commit instead of hedge.

The full Vault — all 50 prompts, 5 `.cursorrules` files, and 3 `CLAUDE.md` starters (Go, Elixir, AI-agent projects) — is **[free on sublimecoding.com](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompts_index&utm_campaign=vault)**.

## The prompts

### Code Review

- **[Blast Radius Analysis](./code-review-blast-radius.md)** — Before merging a PR that touches shared infrastructure.
- **[Security-First Review](./code-review-security-first.md)** — Before merging anything that touches auth, input handling, or external IO.
- **[Database Migration Safety Review](./code-review-migration-safety.md)** — Reviewing any DDL change against a live, large production database.

### Debugging

- **[Hypothesis-Driven Debugging](./debugging-hypothesis-driven.md)** — When you've been staring at a bug for 30 minutes and need a reset.
- **[Reproduce a Race Condition Reliably](./debugging-race-condition.md)** — When the bug appears once a week in production but never on your laptop.
- **[Production Incident: First 10 Minutes](./debugging-production-incident.md)** — Page just fired. You're alone. What now.

### Refactoring

- **[Decompose a Long Function the Right Way](./refactoring-long-functions.md)** — 200-line function that does sequential things.
- **[Make Illegal States Unrepresentable](./refactoring-illegal-states.md)** — When a struct has 4 optional fields and only some combos are valid.
- **[Untangle a God Class](./refactoring-god-class.md)** — 1500-line UserService that does everything.

### System Design

- **[Design Idempotent APIs](./system-design-idempotency.md)** — Any API that mutates state and might be retried (i.e. all of them).
- **[Pick the Right Queue](./system-design-pick-a-queue.md)** — When you need async processing and have to choose between Kafka, SQS, Pub/Sub, RabbitMQ, or a DB-backed queue.
- **[Design a Rate Limiter](./system-design-rate-limiter.md)** — Adding rate limits to a public or partner API.

### Docs & PRs

- **[PR Description from Diff](./docs-pr-description.md)** — Same as code-review-10, used for self-authoring not review.
- **[Architecture Decision Record](./docs-adr.md)** — When a non-trivial decision deserves a written record.
- **[Postmortem Draft from Incident Notes](./docs-postmortem.md)** — Writing the postmortem the day after, while context is fresh.

## How to use these

Drop the prompt into your chat or system prompt. Replace the `<paste here>` marker with your diff, function, endpoint, or context. Most are tuned to refuse hedging — if the model gives you a wishy-washy answer, paste the prompt again with "Pick one and commit." appended.

These prompts assume you've done the basics: written the failing test, run the linter, read the error twice. They're for the part where the work is actually hard.

---

**[Get all 50 prompts free →](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompts_index&utm_campaign=vault)**  ·  **[sublimecoding.com](https://sublimecoding.com?utm_source=github&utm_medium=prompts_index&utm_campaign=brand)**  ·  **[Consulting](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompts_index&utm_campaign=consulting)**
