# CLAUDE.md — [Service Name]

> Drop this at the root of your Go service. Claude Code reads it on every run.
> Replace everything in `[brackets]` with your specifics. Delete what doesn't apply.

## Project overview

[One sentence: what this service does and who calls it.]

- **Runtime:** Go [1.22+]
- **Primary datastore:** [Postgres / DynamoDB / Spanner / ...]
- **Message bus (if any):** [Kafka / RabbitMQ / SQS / NATS / none]
- **Deployment target:** [GKE / ECS / Fly / bare metal]
- **Observability:** [OpenTelemetry → Datadog / Honeycomb / Prometheus]

## Repository layout

```
cmd/<binary>/       Entry points. main.go only. No business logic here.
internal/           Private packages. Anything that isn't a stable public API.
internal/<domain>/  One subdirectory per bounded context.
pkg/                Reserved for code we'd publish to other repos. Currently empty.
api/                Protobuf / OpenAPI specs.
migrations/         SQL migrations, numbered, never rewritten after merge.
scripts/            Dev / CI helpers. Bash only. Keep them under 50 lines.
```

Anything in `internal/` is off-limits to other repos. Do not move code to `pkg/` without an ADR.

## Code conventions

- **Formatting:** `gofmt` and `goimports`. Non-negotiable. Run before commit.
- **Lint:** `golangci-lint run` must pass. Config is `.golangci.yml`. Do not disable rules locally without a `//nolint:<rule> // reason` comment.
- **Naming:** Go idiomatic. Short receivers (`u *User`, not `user *User`). Package names singular and lowercase. Avoid stutter (`user.User` is fine, `userpkg.UserService` is not).
- **Files:** One concept per file. If a file grows past ~400 lines, split by responsibility, not by line count.
- **Comments:** Doc comments on every exported identifier, full sentences ending in periods. Inline comments only when the *why* isn't obvious from the code.

## Error handling

- Errors are values. Return them; do not log-and-continue.
- Wrap with `fmt.Errorf("doing X: %w", err)` to preserve the chain. The verb is what *this* function was doing, not what failed.
- Sentinel errors live at the top of the package they originate in. Use `errors.Is` / `errors.As` at boundaries, never string-match on `err.Error()`.
- Public APIs return typed errors when callers might branch on them. Internal helpers can return `error` plain.
- `panic` only for truly impossible states (invariant violations during init). Never for user input or upstream failures.

## Logging

- Structured only. We use [`slog` / `zap` / `zerolog`]. No `fmt.Println`, no `log.Printf`.
- Log levels: `error` for things a human investigates, `warn` for degraded-but-handled, `info` for state transitions, `debug` for traces.
- Include `request_id`, `user_id` (or `tenant_id`), and the relevant entity ID on every log inside a request path.
- Never log secrets, full request bodies, or PII. There's a redaction helper in `internal/log/redact.go` — use it.

## Testing

- **Default:** table-driven tests with `t.Run(name, func(t *testing.T) { ... })`.
- **Coverage target:** [80%] on `internal/`, no target on `cmd/`.
- **Naming:** `TestXxx_<behavior>` for unit, `TestXxx_Integration` for ones that hit a database.
- **Test data:** factories in `internal/testdata/`, not fixtures pasted inline.
- **DB tests:** real Postgres in a Docker container via `testcontainers-go`. Do not mock the database. We got burned by mocked-passing / migration-broken before.
- **HTTP tests:** `httptest.Server`, not mocked clients.
- **Flakes:** any flaky test is a bug. Quarantine + file an issue same day. Do not re-run CI to "see if it passes."

## Common commands

```bash
make build           # Build all binaries into ./bin/
make test            # Unit tests with race detector
make test-integration # Integration tests (requires Docker)
make lint            # golangci-lint
make migrate         # Apply pending migrations against $DATABASE_URL
make run             # Run the main service locally with .env loaded
```

If a command isn't in the Makefile, add it there rather than running it ad-hoc.

## Database & migrations

- Migrations live in `migrations/` and are applied with [`golang-migrate` / `goose` / `sqlc`].
- One migration = one logical change. Always write the down migration. Never edit a merged migration — write a new one.
- Adding a column: nullable first, backfill, then NOT NULL in a follow-up migration. No `NOT NULL` + default on tables over 1M rows in a single migration.
- Indexes on production tables go in with `CONCURRENTLY` if Postgres.

## Dependencies

- Add a new dependency only when the alternative is more than ~100 lines of obvious code we'd otherwise vendor.
- Standard library and `golang.org/x/...` first. Then well-known third-party. Then evaluate carefully.
- Run `go mod tidy` before commit. PRs that bloat `go.sum` without a reason will be sent back.

## Things we don't do

- No `init()` functions outside of `main` and `_test.go` files. Init order is implicit and bites later.
- No `context.Background()` inside a request path. Plumb the request context.
- No global mutable state. If you need a singleton, inject it.
- No `interface{}` / `any` in domain code. Define the interface where you consume it, not where you produce it.
- No "smart" generics. If a generic helper makes the call site harder to read, write the concrete version.
- No silent retries. Retries are explicit, bounded, and instrumented.

## Observability

- Every external call (DB, HTTP, queue) goes inside a span. Use the helper in `internal/obs/trace.go`.
- Metric names follow `<service>_<resource>_<action>_<unit>` — e.g. `payments_charges_attempted_total`.
- The "is it up?" answer is the `/healthz` endpoint. The "is it healthy?" answer is the SLO dashboard at [link].

## When in doubt

1. Read the nearest existing file in the same package. Match its style.
2. If there isn't one, read another service in the org with similar shape.
3. If still unclear, ask in [#eng-help] or open a draft PR with a question in the description.

Do not invent a new pattern silently. If you think a new pattern is warranted, propose it in an ADR under `docs/adrs/`.

---

> This `CLAUDE.md` is a starter from [The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault).
> The full Vault includes Elixir and AI-agent starters, 50 prompts, and 5 `.cursorrules` files. — [sublimecoding.com](https://sublimecoding.com)
