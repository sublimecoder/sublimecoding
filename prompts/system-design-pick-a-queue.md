# System Design — Pick the Right Queue

A staff-level System Design prompt for Claude Code, Cursor, and other AI coding assistants.

**Use it when:** When you need async processing and have to choose between Kafka, SQS, Pub/Sub, RabbitMQ, or a DB-backed queue.

**Why it works:** Queue choices get litigated forever. Forcing a per-option fit score and a single recommendation cuts the bikeshedding.

---

```
Help me choose a queue/streaming technology for this workload.

Workload:
<describe: throughput, message size, latency, ordering needs, retention, consumers>

Operational context:
<cloud, team experience, existing infra, budget>

Compare these options for THIS workload (not in the abstract):
- Kafka (managed: MSK, Confluent, Aiven)
- Cloud-native pub/sub (SQS, GCP Pub/Sub, Azure Service Bus)
- Broker (RabbitMQ, NATS)
- DB-backed (Postgres SKIP LOCKED, river, oban, sidekiq)

For each: fit (1-10), the one thing that makes it right or wrong here, monthly ops cost.
End with a single recommendation and what would make you change your mind.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
