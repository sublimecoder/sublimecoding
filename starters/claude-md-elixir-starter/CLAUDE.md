# CLAUDE.md — [App Name]

> Drop this at the root of your Elixir / Phoenix repo. Claude Code reads it on every run.
> Replace everything in `[brackets]` with your specifics. Delete what doesn't apply.

## Project overview

[One sentence: what this app does and who calls it.]

- **Elixir:** [1.16+] · **Erlang/OTP:** [26+]
- **Framework:** [Phoenix 1.7+ / pure OTP / Nerves]
- **Shape:** [Single Mix project / Umbrella with apps/ subtree]
- **Web layer (if any):** [Phoenix LiveView / Phoenix Controllers / Absinthe GraphQL]
- **Primary datastore:** [Postgres via Ecto / DynamoDB / Mnesia]
- **Background work:** [Oban / Broadway / GenStage / none]
- **Deployment target:** [Releases on Fly.io / Gigalixir / Kubernetes / bare metal]
- **Observability:** [Telemetry → AppSignal / Datadog / Honeycomb / PromEx]

## Repository layout

```
# Umbrella shape:
apps/<app>_core/        Domain logic. No web, no persistence concerns leaking in.
apps/<app>_web/         Phoenix endpoint, controllers, LiveViews, channels.
apps/<app>_workers/     Oban / Broadway pipelines. No business rules here.
config/                 Shared config. Runtime values in runtime.exs only.
priv/repo/migrations/   Ecto migrations. Numbered, never rewritten.
priv/static/            Public static assets.
test/                   Mirror the lib/ tree exactly.
```

If single-app (non-umbrella), collapse `apps/<app>_core/lib/` into `lib/<app>/` with the same internal boundaries (`<app>/accounts/`, `<app>/billing/`, etc.) — one directory per context.

## Code conventions

- **Formatting:** `mix format` is non-negotiable. Run before commit. The `.formatter.exs` is the source of truth — do not override locally.
- **Lint:** `mix credo --strict` must pass. `mix dialyzer` must pass on `main`. PRs run both in CI.
- **Naming:** Modules are `PascalCase`. Functions and variables `snake_case`. Predicate functions end in `?` (`User.admin?/1`). Bang functions raise (`User.fetch!/1`); their non-bang siblings return `{:ok, _} | {:error, _}`.
- **Module size:** If a module passes ~300 lines, split by responsibility (not by line count). Public functions at the top, private at the bottom, in call order.
- **Doc comments:** `@moduledoc` on every public module. `@doc` on every public function. `@spec` on public functions that take or return non-trivial shapes.

## Pattern matching first

- Use pattern matching, not `case`-on-tag.
- `with` is the default for sequencing operations that can fail. Avoid `try`/`rescue` unless catching a known raise from a library you don't control.
- Tagged tuples (`{:ok, value}` / `{:error, reason}`) are the contract. Don't return raw values from things that can fail.
- Multi-clause function heads beat `cond` / nested `if`.

## Contexts & boundaries (Phoenix)

- A context is a public API surface for a domain. Web code calls `Accounts.create_user/1`, never `Accounts.User.changeset/2` directly.
- Schemas (`Ecto.Schema`) and changesets stay private to the context.
- One context per bounded concept — `Accounts`, `Billing`, `Notifications`. Not one context per table.
- Cross-context calls go through the other context's public API. No reaching into `OtherContext.Schema` from outside.

## OTP & processes

- A process is the answer when you need: long-lived state, isolation, supervised work, or rate-limiting. **Not** when you need: a place to put a function.
- GenServer state is **internal**. Expose it via public functions on the GenServer's module — never have callers send raw messages.
- Every supervised process has an `init/1` that can fail fast. Crash-and-restart is the design, not a bug.
- Use `Task.Supervisor` for fire-and-forget. Use `Task.async_stream/3` for parallel maps. Don't roll your own.

## Ecto

- Changesets live on the schema module. Validation, casting, constraints — all there.
- Repo calls live in the context, never in controllers or LiveViews.
- Use `Ecto.Multi` for any operation that touches more than one row across more than one table. Two `Repo` calls in a row is usually a `Multi` waiting to happen.
- Migrations: one logical change per migration, both `up` and `down` defined. Never edit a merged migration.

## Testing

- **Framework:** ExUnit. Use `async: true` everywhere it's safe.
- **Coverage target:** [80%] on `apps/<app>_core/`. No target on the web app.
- **Test data:** factories via [`ex_machina`] or hand-rolled helpers in `test/support/`. No inline fixtures.
- **DB tests:** Ecto sandbox in `:manual` mode. Real Postgres. Do not mock the database.
- **External services:** stub via [`Mox`] with explicit behaviours, not by replacing modules at runtime.
- **Property tests:** for parsers, serializers, and anything with non-obvious invariants — use `StreamData`.
- **Flakes:** any flaky test is a bug. Quarantine + file an issue same day. Do not re-run CI to "see if it passes."

## Common commands

```bash
mix deps.get           # Install dependencies
mix ecto.setup         # Create + migrate + seed
mix ecto.migrate       # Apply pending migrations
mix test               # All tests (excludes :integration tag by default)
mix test --include integration
mix format             # Apply formatter
mix credo --strict     # Style + complexity lint
mix dialyzer           # Type analysis
mix phx.server         # Run Phoenix locally
iex -S mix             # REPL with app loaded
```

If a command isn't in this list, add a Mix alias rather than running it ad-hoc.

## Releases & runtime config

- `mix release` is the deployment unit. No `mix phx.server` in production.
- All runtime config lives in `config/runtime.exs`, sourced from env vars.
- `config/config.exs` is **compile-time only** — anything that varies between environments belongs in `runtime.exs`.
- Secrets come from the platform's secret manager (Fly secrets, AWS SSM, GCP Secret Manager). Never `.env` in production.

## Observability

- `:telemetry.execute/3` on every domain event worth knowing about. Define event names as module attributes in the context that emits them.
- LiveView and Phoenix already emit standard events — wire them to your metrics backend via `Telemetry.Metrics`.
- Logs are structured. `Logger.metadata/1` to add `request_id`, `user_id`, `tenant_id`. No `IO.inspect/2` in committed code (it's fine in `iex`).

## Things we don't do

- No `try`/`rescue` around our own code. Either pattern match `{:error, _}`, or let it crash.
- No `:erlang.send/2` to a process by name from outside a `GenServer.call/2`. If you need to message a server, expose a function.
- No `Process.sleep/1` in tests. Use `assert_eventually` or message-driven sync.
- No "service modules" that wrap a single function. Just have the function in the context.
- No `Application.get_env/2` at function call time. Read config at boot or pass it in.
- No `Mix.env()` checks in `lib/` — only in `config/` and `mix.exs`.

## When in doubt

1. Read the nearest existing module in the same context. Match its shape.
2. If there isn't one, read the equivalent module in another context.
3. If still unclear, open a draft PR with a question in the description, or ask in [#eng-help].

Do not invent a new pattern silently. If you think a new pattern is warranted, propose it in an ADR under `docs/adrs/`.

---

> This `CLAUDE.md` is a starter from [The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault).
> The full Vault includes Go and AI-agent starters, 50 prompts, and 5 `.cursorrules` files. — [sublimecoding.com](https://sublimecoding.com)
