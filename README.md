# Claude Code Prompts for Senior Engineers — Free Prompt Library

**[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault?utm_source=github&utm_medium=readme_hero&utm_campaign=vault)** by **SublimeCoding** — 50 production-grade prompts for Claude Code and Cursor, built at staff level: code review, debugging, refactoring, system design, and docs. Plus 5 drop-in `.cursorrules` files, 3 `CLAUDE.md` starters (Go, Elixir, AI-agent projects), an `AGENTS.md` starter, and a Notion blueprint.

**Free · no app · no login · lifetime updates.**

→ **[Get the Vault, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=readme_hero&utm_campaign=vault)**  ·  **[15 sample prompts →](./prompts)**  ·  **[FAQ →](./FAQ.md)**

> ⭐ If these prompts save you a production bug or a wasted hour, star the repo — it's how other engineers find it.

## Contents

- [Claude Code Prompts](#claude-code-prompts)
- [Cursor Prompts for Senior Engineers](#cursor-prompts-for-senior-engineers)
- [AI Code Review Prompts](#ai-code-review-prompts)
- [CLAUDE.md & AGENTS.md Templates](#claudemd--agentsmd-templates)
- [.cursorrules for Senior Engineers](#cursorrules-for-senior-engineers)

## Claude Code Prompts

15 free, production-tested Claude Code prompts for senior engineers — [browse them in `/prompts`](./prompts). Each encodes how a staff engineer actually uses AI: structured thinking over pattern-matched answers, named failure modes, and a model that commits instead of hedges.

- **Debugging** — [production incident](./prompts/debugging-production-incident.md), [race condition](./prompts/debugging-race-condition.md), [hypothesis-driven](./prompts/debugging-hypothesis-driven.md)
- **Refactoring** — [god class](./prompts/refactoring-god-class.md), [illegal states](./prompts/refactoring-illegal-states.md), [long functions](./prompts/refactoring-long-functions.md)
- **System design** — [idempotency](./prompts/system-design-idempotency.md), [rate limiter](./prompts/system-design-rate-limiter.md), [pick a queue](./prompts/system-design-pick-a-queue.md)
- **Docs & PRs** — [ADR](./prompts/docs-adr.md), [postmortem](./prompts/docs-postmortem.md), [PR description](./prompts/docs-pr-description.md)

## Cursor Prompts for Senior Engineers

Every prompt here is tool-agnostic — they work in Cursor exactly as they do in Claude Code. For Cursor specifically, start with the [senior-engineer `.cursorrules`](./cursorrules/senior-engineer.cursorrules), then layer in the task prompts above.

## AI Code Review Prompts

Staff-level AI code review prompts that fight the way models actually fail at review:

- **[Security-first review](./prompts/code-review-security-first.md)** — auth, input handling, external I/O.
- **[Blast radius analysis](./prompts/code-review-blast-radius.md)** — before merging changes to shared infrastructure.
- **[Database migration safety](./prompts/code-review-migration-safety.md)** — DDL against a live, large production DB.

## CLAUDE.md & AGENTS.md Templates

- **[`AGENTS.md` starter](./AGENTS.md)** — production-grade agent-instructions template (works as `CLAUDE.md` too).
- **`CLAUDE.md` starters** — drop them into any repo and the agent understands your conventions on the first message:
  - **[Go services →](https://github.com/sublimecoder/claude-md-go-starter)**
  - **[Elixir / Phoenix →](https://github.com/sublimecoder/claude-md-elixir-starter)**
  - **[AI agent projects →](https://github.com/sublimecoder/claude-md-ai-agents-starter)**

## .cursorrules for Senior Engineers

Free, staff-level `.cursorrules` — each works in Cursor, Claude Code, Windsurf, or any rules-file tool:

- **[senior-engineer.cursorrules](./cursorrules/senior-engineer.cursorrules)** — the baseline posture: read-first, trace every change, handle the error path, verify before "done".
- **[go-microservices.cursorrules](./cursorrules/go-microservices.cursorrules)** — Go services: context propagation, error wrapping, bounded concurrency, graceful shutdown, table tests.
- **[elixir.cursorrules](./cursorrules/elixir.cursorrules)** — Elixir/Phoenix: OTP supervision, `with` pipelines, Ecto changeset discipline, context boundaries, let-it-crash.
- **[security.cursorrules](./cursorrules/security.cursorrules)** — production security: untrusted-input handling, secrets hygiene, authz at every boundary, prompt-injection containment.

The Vault bundles all of these (plus the AI-agent ruleset), the 50 prompts, and the `CLAUDE.md` starters in one download.

→ **[Get all 50 prompts + every `.cursorrules` file, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=readme_body&utm_campaign=vault)**

---

### Who made this — Jared Smith, Staff Software Engineer

Production AI. Distributed systems. Security.

13+ years shipping software. 100K+ users on live AI products. $400M+ in fintech assets protected. 40K+ telematics devices streaming.

Director of Information Security at Lavender. Backend at BlockFi. Elixir at AAMP Global. Co-founded a startup, scaled engineering from 1 to 15.

Bias toward clarity, observability, and predictable failure. The prompts here came from the real problem of teaching 14 other engineers to use AI without making their code worse — which is where the failure-mode framing comes from.

---

### Featured writing

- **[How I Prompt Claude as a Staff Engineer (50 Prompts I Actually Use)](https://sublimecoding.com/blog/staff-engineer-claude-prompts)** — the prompts behind the Vault and how I actually use them.
- **[Ruflo (formerly Claude Flow): An Honest Deep Dive](https://sublimecoding.com/blog/ruflo-claude-flow-multi-agent-deep-dive)** — 45K+ stars, 700K+ downloads. What it does well, and where it falls down.
- **[The Claude Code Resource Bible: 46 Tools Worth Knowing in 2026](https://sublimecoding.com/blog/claude-code-resource-bible)** — official tools, MCP servers, agents, automation. Curated, not a link dump.

#### Latest posts

<!-- BLOG-POST-LIST:START -->
- [TDD With Claude Code in Elixir: What Holds Up](https://sublimecoding.com/blog/tdd-claude-code-elixir)
- [Security Engineer or vCISO? Your First Hire, by Stage](https://sublimecoding.com/blog/security-engineer-or-vciso-first-hire)
- [What I Put in CLAUDE.md After 50 Commits With It](https://sublimecoding.com/blog/claude-md-after-50-commits)
- [Secrets Management for AI Agents on Small Teams](https://sublimecoding.com/blog/ai-agent-secrets-management)
- [Streaming LLM Tokens in LiveView, the 2026 Way](https://sublimecoding.com/blog/streaming-llm-tokens-liveview-2026)
<!-- BLOG-POST-LIST:END -->

→ More at **[sublimecoding.com/blog](https://sublimecoding.com/blog)**

---

### Consulting — work with me

Selective, senior engagements where a Staff/Principal-level brain moves the needle:

- **Production AI delivery** — ship LLM features that survive real users, with the evals, guardrails, and cost discipline to back them.
- **Backend & distributed systems at scale** — the architecture, reliability, and observability work that keeps growth from breaking you.
- **Fractional security & compliance leadership (vCISO)** — SOC 2, AWS hardening, and an AI data-handling posture your enterprise prospects will actually trust.

→ **[Book a 30-min intro call](https://sublimecoding.com/consulting)** · [What 90 days of a fractional security engagement actually looks like](https://sublimecoding.com/blog/what-a-fractional-security-engagement-actually-looks-like)

---

### Stack

Go, Elixir, Ruby. GCP, AWS, Azure. Postgres, Kafka, RabbitMQ. Claude Code, Cursor, Codex daily since 2023.

### Find me

[sublimecoding.com](https://sublimecoding.com) · [@sublimecoder](https://x.com/sublimecoder) · [LinkedIn](https://www.linkedin.com/in/jared-smith-ab834565/) · jared@sublimecoding.com
