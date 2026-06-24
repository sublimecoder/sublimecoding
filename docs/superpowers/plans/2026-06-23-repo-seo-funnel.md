# Repo-as-SEO-Asset & Sales-Funnel Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Turn this GitHub prompt repo into an exact-match-keyword, TOC-structured prompt library that ranks for ~15 under-defended long-tail queries and funnels visitors to `/vault` → `/consulting`.

**Architecture:** This is a Markdown content repo — there is no test framework. "Tests" here are **grep/shell assertions** that verify the SEO-critical invariants (exact-match phrase in the H1, snippet in first ~160 chars, UTM-tagged CTAs present). Each task: make the edit → run the assertion → commit. Content tasks come first; the repo rename (W1) runs last so it doesn't disrupt mid-work.

**Tech Stack:** Markdown, `git`, `gh` CLI (GitHub repo metadata), `grep`/`awk` (assertions).

**Spec:** `docs/superpowers/specs/2026-06-23-repo-seo-funnel-design.md`

**Open-item decisions baked in:**
- Slug: `claude-code-prompts-for-senior-engineers`
- W3 v1: `cursorrules/senior-engineer.cursorrules` + `AGENTS.md` starter (Go/Elixir/security cursorrules → Future Work)
- AGENTS.md starter: included now

---

## File map

| File | Action | Responsibility |
|---|---|---|
| `prompts/*.md` (15) | Modify H1 + subtitle | Exact-match query in first ~160 chars |
| `prompts/*.md` (15) | Modify footer | Add consulting CTA + UTM tags |
| `prompts/README.md` | Modify | UTM on outbound CTAs |
| `cursorrules/senior-engineer.cursorrules` | Create | Opens "cursor rules for senior engineers" gap |
| `AGENTS.md` | Create | Opens "AGENTS.md template" gap |
| `README.md` (root) | Rewrite | TOC + verbatim H2 cluster sections + CTAs |
| repo metadata | Modify (gh) | Slug, About, topics |

---

## Task 1: Rewrite Code Review prompt headers

**Files:**
- Modify: `prompts/code-review-security-first.md` (lines 1-3)
- Modify: `prompts/code-review-blast-radius.md` (lines 1-3)
- Modify: `prompts/code-review-migration-safety.md` (lines 1-3)

- [ ] **Step 1: Edit `code-review-security-first.md`** — replace the first two non-blank lines.

Replace:
```markdown
# Code Review — Security-First Review

A staff-level Code Review prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Security Review Prompt

A staff-level security-first code review prompt for Claude Code, Cursor, and other AI coding assistants — run it before merging anything that touches auth, input handling, or external I/O.
```

- [ ] **Step 2: Edit `code-review-blast-radius.md`**

Replace:
```markdown
# Code Review — Blast Radius Analysis

A staff-level Code Review prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# AI Code Review Prompt — Blast Radius Analysis

A staff-level blast radius analysis prompt for Claude Code, Cursor, and other AI coding assistants — before merging a PR that touches shared infrastructure.
```

- [ ] **Step 3: Edit `code-review-migration-safety.md`**

Replace:
```markdown
# Code Review — Database Migration Safety Review

A staff-level Code Review prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Migration Safety Review Prompt

A staff-level database migration safety review prompt for Claude Code, Cursor, and other AI coding assistants — for any DDL change against a live, large production database.
```

- [ ] **Step 4: Verify the exact-match phrases are in the H1s**

Run:
```bash
cd /Users/jsmith/code/sublimecoding-marketing
grep -l "Claude Code Security Review Prompt" prompts/code-review-security-first.md && \
grep -l "AI Code Review Prompt — Blast Radius" prompts/code-review-blast-radius.md && \
grep -l "Claude Code Migration Safety Review Prompt" prompts/code-review-migration-safety.md
```
Expected: all three filenames printed (one per match).

- [ ] **Step 5: Commit**

```bash
git add prompts/code-review-*.md
git commit -m "seo: keyword-optimize Code Review prompt headers"
```

---

## Task 2: Rewrite Debugging prompt headers

**Files:**
- Modify: `prompts/debugging-production-incident.md` (lines 1-3)
- Modify: `prompts/debugging-race-condition.md` (lines 1-3)
- Modify: `prompts/debugging-hypothesis-driven.md` (lines 1-3)

- [ ] **Step 1: Edit `debugging-production-incident.md`**

Replace:
```markdown
# Debugging — Production Incident: First 10 Minutes

A staff-level Debugging prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Production Debugging Prompt

A staff-level production debugging prompt for Claude Code, Cursor, and other AI coding assistants — the first 10 minutes after a page fires and you're alone.
```

- [ ] **Step 2: Edit `debugging-race-condition.md`**

Replace:
```markdown
# Debugging — Reproduce a Race Condition Reliably

A staff-level Debugging prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Race Condition Debugging Prompt

A staff-level race condition debugging prompt for Claude Code, Cursor, and other AI coding assistants — reproduce the bug that shows up weekly in prod but never on your laptop.
```

- [ ] **Step 3: Edit `debugging-hypothesis-driven.md`**

Replace:
```markdown
# Debugging — Hypothesis-Driven Debugging

A staff-level Debugging prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Debugging Prompt — Hypothesis-Driven

A staff-level hypothesis-driven debugging prompt for Claude Code, Cursor, and other AI coding assistants — when you've stared at a bug for 30 minutes and need a reset.
```

- [ ] **Step 4: Verify**

Run:
```bash
grep -l "Claude Code Production Debugging Prompt" prompts/debugging-production-incident.md && \
grep -l "Claude Code Race Condition Debugging Prompt" prompts/debugging-race-condition.md && \
grep -l "Claude Code Debugging Prompt — Hypothesis-Driven" prompts/debugging-hypothesis-driven.md
```
Expected: all three filenames printed.

- [ ] **Step 5: Commit**

```bash
git add prompts/debugging-*.md
git commit -m "seo: keyword-optimize Debugging prompt headers"
```

---

## Task 3: Rewrite Refactoring prompt headers

**Files:**
- Modify: `prompts/refactoring-god-class.md` (lines 1-3)
- Modify: `prompts/refactoring-illegal-states.md` (lines 1-3)
- Modify: `prompts/refactoring-long-functions.md` (lines 1-3)

- [ ] **Step 1: Edit `refactoring-god-class.md`**

Replace:
```markdown
# Refactoring — Untangle a God Class

A staff-level Refactoring prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code God Class Refactoring Prompt

A staff-level god class refactoring prompt for Claude Code, Cursor, and other AI coding assistants — untangle a 1500-line service that does everything.
```

- [ ] **Step 2: Edit `refactoring-illegal-states.md`**

Replace:
```markdown
# Refactoring — Make Illegal States Unrepresentable

A staff-level Refactoring prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Refactoring Prompt — Make Illegal States Unrepresentable

A staff-level refactoring prompt for Claude Code, Cursor, and other AI coding assistants — make illegal states unrepresentable when a struct has optional fields and only some combos are valid.
```

- [ ] **Step 3: Edit `refactoring-long-functions.md`**

Replace:
```markdown
# Refactoring — Decompose a Long Function the Right Way

A staff-level Refactoring prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Refactoring Prompt — Decompose a Long Function

A staff-level long-function refactoring prompt for Claude Code, Cursor, and other AI coding assistants — decompose a 200-line function that does sequential things.
```

- [ ] **Step 4: Verify**

Run:
```bash
grep -l "Claude Code God Class Refactoring Prompt" prompts/refactoring-god-class.md && \
grep -l "Make Illegal States Unrepresentable" prompts/refactoring-illegal-states.md && \
grep -l "Decompose a Long Function" prompts/refactoring-long-functions.md
```
Expected: all three filenames printed.

- [ ] **Step 5: Commit**

```bash
git add prompts/refactoring-*.md
git commit -m "seo: keyword-optimize Refactoring prompt headers"
```

---

## Task 4: Rewrite System Design prompt headers

**Files:**
- Modify: `prompts/system-design-idempotency.md` (lines 1-3)
- Modify: `prompts/system-design-rate-limiter.md` (lines 1-3)
- Modify: `prompts/system-design-pick-a-queue.md` (lines 1-3)

- [ ] **Step 1: Edit `system-design-idempotency.md`**

Replace:
```markdown
# System Design — Design Idempotent APIs

A staff-level System Design prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Idempotency Design Prompt

A staff-level idempotency design prompt for Claude Code, Cursor, and other AI coding assistants — for any API that mutates state and might be retried.
```

- [ ] **Step 2: Edit `system-design-rate-limiter.md`**

Replace:
```markdown
# System Design — Design a Rate Limiter

A staff-level System Design prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Rate Limiter Design Prompt

A staff-level rate limiter design prompt for Claude Code, Cursor, and other AI coding assistants — adding rate limits to a public or partner API.
```

- [ ] **Step 3: Edit `system-design-pick-a-queue.md`**

Replace:
```markdown
# System Design — Pick the Right Queue

A staff-level System Design prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code System Design Prompt — Pick the Right Queue

A staff-level system design prompt for Claude Code, Cursor, and other AI coding assistants — choose between Kafka, SQS, Pub/Sub, RabbitMQ, or a DB-backed queue.
```

- [ ] **Step 4: Verify**

Run:
```bash
grep -l "Claude Code Idempotency Design Prompt" prompts/system-design-idempotency.md && \
grep -l "Claude Code Rate Limiter Design Prompt" prompts/system-design-rate-limiter.md && \
grep -l "Claude Code System Design Prompt — Pick the Right Queue" prompts/system-design-pick-a-queue.md
```
Expected: all three filenames printed.

- [ ] **Step 5: Commit**

```bash
git add prompts/system-design-*.md
git commit -m "seo: keyword-optimize System Design prompt headers"
```

---

## Task 5: Rewrite Docs & PRs prompt headers

**Files:**
- Modify: `prompts/docs-adr.md` (lines 1-3)
- Modify: `prompts/docs-postmortem.md` (lines 1-3)
- Modify: `prompts/docs-pr-description.md` (lines 1-3)

- [ ] **Step 1: Edit `docs-adr.md`**

Replace:
```markdown
# Docs & PRs — Architecture Decision Record

A staff-level Docs & PRs prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code ADR Prompt — Architecture Decision Record

A staff-level architecture decision record (ADR) prompt for Claude Code, Cursor, and other AI coding assistants — when a non-trivial decision deserves a written record.
```

- [ ] **Step 2: Edit `docs-postmortem.md`**

Replace:
```markdown
# Docs & PRs — Postmortem Draft from Incident Notes

A staff-level Docs & PRs prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code Postmortem Prompt

A staff-level incident postmortem prompt for Claude Code, Cursor, and other AI coding assistants — draft the postmortem the day after, while context is fresh.
```

- [ ] **Step 3: Edit `docs-pr-description.md`**

Replace:
```markdown
# Docs & PRs — PR Description from Diff

A staff-level Docs & PRs prompt for Claude Code, Cursor, and other AI coding assistants.
```
With:
```markdown
# Claude Code PR Description Prompt

A staff-level PR description prompt for Claude Code, Cursor, and other AI coding assistants — generate a reviewable PR description from your diff.
```

- [ ] **Step 4: Verify**

Run:
```bash
grep -l "Claude Code ADR Prompt" prompts/docs-adr.md && \
grep -l "Claude Code Postmortem Prompt" prompts/docs-postmortem.md && \
grep -l "Claude Code PR Description Prompt" prompts/docs-pr-description.md
```
Expected: all three filenames printed.

- [ ] **Step 5: Commit**

```bash
git add prompts/docs-*.md
git commit -m "seo: keyword-optimize Docs & PRs prompt headers"
```

---

## Task 6: Upgrade CTA footers (consulting link + UTM) across all 15 prompts

The 15 prompt files share an identical final CTA line. This task adds a consulting CTA and UTM tags so referral traffic is attributable.

**Files:**
- Modify: all 15 `prompts/*.md` (final CTA line)

- [ ] **Step 1: Replace the CTA line AND tag the in-paragraph vault link in every prompt file**

Each file contains two bare links to tag: the in-paragraph mention `...AI Prompt Vault](https://sublimecoding.com/vault)** —` and the final CTA line. This does both, plus adds the consulting CTA:
```bash
cd /Users/jsmith/code/sublimecoding-marketing
OLD_CTA='→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**'
NEW_CTA='→ **[Get the full Vault, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_footer&utm_campaign=vault)**  ·  **[Consulting for production AI & scale](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompt_footer&utm_campaign=consulting)**  ·  **[← all 15 sample prompts](./README.md)**'
for f in prompts/*.md; do
  [ "$(basename "$f")" = "README.md" ] && continue
  python3 - "$f" "$OLD_CTA" "$NEW_CTA" <<'PY'
import sys
path, old_cta, new_cta = sys.argv[1], sys.argv[2], sys.argv[3]
s = open(path, encoding="utf-8").read()
# 1) structural: replace the final CTA line (its vault link is already tagged in new_cta)
assert old_cta in s, f"NO-MATCH CTA {path}"
s = s.replace(old_cta, new_cta)
# 2) tag the remaining bare in-paragraph vault link
s = s.replace("(https://sublimecoding.com/vault)**",
              "(https://sublimecoding.com/vault?utm_source=github&utm_medium=prompt_body&utm_campaign=vault)**")
# safety: no bare vault/consulting links should remain
assert "sublimecoding.com/vault)" not in s and "sublimecoding.com/consulting)" not in s, f"BARE LINK LEFT {path}"
open(path, "w", encoding="utf-8").write(s)
print("updated", path)
PY
done
```
Expected: 15 lines printed, all `updated prompts/...`. If any file raises an AssertionError, STOP and inspect that file.

- [ ] **Step 2: Verify consulting CTA + UTM present, and zero bare links remain, in all 15**

Run:
```bash
echo "consulting links: $(grep -l 'utm_campaign=consulting' prompts/*.md | grep -v 'README.md' | wc -l)"
echo "vault utm links:  $(grep -l 'utm_campaign=vault' prompts/*.md | grep -v 'README.md' | wc -l)"
echo "bare links: $(grep -rE 'sublimecoding\.com/(vault|consulting)\)' prompts/*.md | grep -v 'README.md' | wc -l)"
```
Expected: consulting `15`, vault `15`, bare `0`.

- [ ] **Step 3: Commit**

```bash
git add prompts/*.md
git commit -m "seo: add consulting CTA + UTM tracking to prompt footers"
```

---

## Task 7: Add UTM tags to `prompts/README.md` outbound CTAs

**Files:**
- Modify: `prompts/README.md` (final CTA line)

- [ ] **Step 1a: Tag the in-body vault link**

Replace (appears once, in the third paragraph):
```markdown
is **[free on sublimecoding.com](https://sublimecoding.com/vault)**.
```
With:
```markdown
is **[free on sublimecoding.com](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompts_index&utm_campaign=vault)**.
```

- [ ] **Step 1b: Tag the final CTA line**

Replace:
```markdown
**[Get all 50 prompts free →](https://sublimecoding.com/vault)**  ·  **[sublimecoding.com](https://sublimecoding.com)**  ·  **[Consulting](https://sublimecoding.com/consulting)**
```
With:
```markdown
**[Get all 50 prompts free →](https://sublimecoding.com/vault?utm_source=github&utm_medium=prompts_index&utm_campaign=vault)**  ·  **[sublimecoding.com](https://sublimecoding.com?utm_source=github&utm_medium=prompts_index&utm_campaign=brand)**  ·  **[Consulting](https://sublimecoding.com/consulting?utm_source=github&utm_medium=prompts_index&utm_campaign=consulting)**
```

- [ ] **Step 2: Verify consulting CTA tagged and zero bare conversion links remain**

Run:
```bash
echo "consulting: $(grep -c 'utm_campaign=consulting' prompts/README.md)"
echo "bare: $(grep -cE 'sublimecoding\.com/(vault|consulting)\)' prompts/README.md)"
```
Expected: consulting `1`, bare `0`.

- [ ] **Step 3: Commit**

```bash
git add prompts/README.md
git commit -m "seo: add UTM tracking to prompts index CTAs"
```

---

## Task 8: Create `cursorrules/senior-engineer.cursorrules`

Opens the wide-open `cursor rules for senior engineers` / `cursor rules staff engineer` queries (no repo on page 1).

**Files:**
- Create: `cursorrules/senior-engineer.cursorrules`

- [ ] **Step 1: Create the directory and file** with this exact content:

```
# .cursorrules — Senior / Staff Engineer
# Free, from The Senior Engineer's AI Prompt Vault — https://sublimecoding.com/vault
# Works in Cursor (.cursorrules), Claude Code (CLAUDE.md), Windsurf (.windsurfrules), and any rules-file tool.

You are pairing with a senior/staff engineer on a production system. Optimize for correctness,
observability, and predictable failure — not for looking productive.

## Default posture
- Read before you write. Inspect the surrounding code, existing patterns, and tests before proposing changes.
- Match the existing style, naming, and idioms even when you'd write it differently.
- Do exactly what was asked. No unrequested abstractions, config, or "while I'm here" refactors.
- When a request is ambiguous, state the interpretations and ask — do not guess past the confusion.

## Changes
- Every changed line must trace to the request. Remove imports/vars/functions your change orphaned.
- Do NOT touch pre-existing dead code or unrelated files — mention them instead.
- Make one logical change at a time. Prefer small, reviewable diffs over large rewrites.

## Correctness & failure modes
- Handle the error path, not just the happy path. Make failures explicit and observable.
- Do not add error handling for cases that cannot occur. No defensive code against impossible inputs.
- Name the failure mode of the thing you're building (retry storms, partial writes, race windows).
- For anything that mutates state and can be retried, make it idempotent.

## Verification
- After a change, run the relevant tests or build. Never claim "done" on untested code.
- Show evidence (command + output), not assertions, when reporting success.
- If you couldn't verify, say so plainly and say what's left.

## Communication
- Lead with the answer. No preamble, no flattery, no filler.
- Surface assumptions and tradeoffs; don't silently choose between materially different options.
- Push back when there's a faster, safer, or simpler path — don't just execute.

# ───────────────────────────────────────────────────────────────────────────
# Want all 5 .cursorrules files + 50 prompts + CLAUDE.md starters? Free, no login:
# https://sublimecoding.com/vault?utm_source=github&utm_medium=cursorrules&utm_campaign=vault
```

- [ ] **Step 2: Verify the file exists and names the target query**

Run:
```bash
test -f cursorrules/senior-engineer.cursorrules && head -2 cursorrules/senior-engineer.cursorrules
```
Expected: the first two `#` comment lines print (file exists).

- [ ] **Step 3: Commit**

```bash
git add cursorrules/senior-engineer.cursorrules
git commit -m "seo: add senior-engineer .cursorrules (opens cursor-rules-for-senior-engineers gap)"
```

---

## Task 9: Create `AGENTS.md` starter

Opens the emerging `AGENTS.md template` / `AGENTS.md example github` query. Uses `<…>` fill-in markers that the END USER replaces (these are template fields, not plan placeholders), matching the style of the repo's existing `CLAUDE.md`.

**Files:**
- Create: `AGENTS.md`

- [ ] **Step 1: Create the file** with this exact content:

```markdown
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
```

- [ ] **Step 2: Verify**

Run: `test -f AGENTS.md && grep -c "AGENTS.md" AGENTS.md`
Expected: a count `>= 2`.

- [ ] **Step 3: Commit**

```bash
git add AGENTS.md
git commit -m "seo: add AGENTS.md starter template (opens AGENTS.md-template gap)"
```

---

## Task 10: Rewrite root `README.md` (TOC + verbatim H2 cluster sections + CTAs)

The root README is what GitHub + Google index for the repo. Add a Contents TOC and verbatim H2 sections per target query cluster, preserving the existing author/E-E-A-T, featured-writing, consulting, and blog-automation blocks.

**Files:**
- Modify: `README.md` (root)

- [ ] **Step 1: Replace the top of the file** — everything from the H1 down to the line `---` that precedes `### Who made this`. Keep everything from `### Who made this — Jared Smith` onward UNCHANGED (author block, featured writing, blog-post-list comments, stack, find-me).

Replace the top section with:
```markdown
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

- **[senior-engineer.cursorrules](./cursorrules/senior-engineer.cursorrules)** — a staff-level baseline ruleset for Cursor. The full Vault adds 4 more (`.cursorrules` for Go, Elixir, security, and AI-agent projects).

→ **[Get all 50 prompts + every `.cursorrules` file, free](https://sublimecoding.com/vault?utm_source=github&utm_medium=readme_body&utm_campaign=vault)**

---
```

Leave the rest of the file (`### Who made this — Jared Smith` through the end) exactly as-is.

- [ ] **Step 2: Verify the TOC + all five H2 cluster headings exist and CTAs carry UTM**

Run:
```bash
for h in "## Claude Code Prompts" "## Cursor Prompts for Senior Engineers" "## AI Code Review Prompts" "## CLAUDE.md & AGENTS.md Templates" "## .cursorrules for Senior Engineers"; do
  grep -qF "$h" README.md && echo "OK: $h" || echo "MISSING: $h"
done
echo "author block intact: $(grep -c 'Who made this — Jared Smith' README.md)"
echo "hero utm present: $(grep -c 'utm_medium=readme_hero' README.md)"
```
Expected: five `OK:` lines, `author block intact: 1`, `hero utm present: 1` (or more).

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "seo: rewrite README with keyword H1, TOC, and verbatim cluster sections"
```

---

## Task 11: Update repo metadata (slug, About, topics)

GitHub metadata changes via the `gh` CLI. The rename runs LAST so it doesn't disrupt the working tree mid-plan. GitHub 301-redirects the old URL, so existing stars/links survive.

**Files:** none (GitHub API via `gh`).

- [ ] **Step 1: Confirm `gh` is authenticated**

Run: `gh auth status`
Expected: "Logged in to github.com" for the `sublimecoder` account. If not, STOP and run `gh auth login`.

- [ ] **Step 2: Set the About description and topics**

Run:
```bash
gh repo edit sublimecoder/sublimecoding-marketing \
  --description "🛠️ Free Claude Code & Cursor prompts for senior engineers — code review, debugging, refactoring, system design, CLAUDE.md & .cursorrules templates. Plus a free Vault of 50 prompts." \
  --add-topic claude-code --add-topic cursor --add-topic cursorrules --add-topic claude \
  --add-topic anthropic --add-topic prompts --add-topic prompt-engineering --add-topic prompt-library \
  --add-topic ai-code-review --add-topic code-review --add-topic claude-md --add-topic llm \
  --add-topic agentic-coding --add-topic senior-engineer --add-topic go --add-topic elixir
```
Expected: no error (command returns silently on success).

- [ ] **Step 3: Verify About + topics**

Run: `gh repo view sublimecoder/sublimecoding-marketing --json description,repositoryTopics`
Expected: JSON shows the new description and the 16 topics.

- [ ] **Step 4: Rename the repo to the exact-match slug**

Run:
```bash
gh repo rename claude-code-prompts-for-senior-engineers \
  --repo sublimecoder/sublimecoding-marketing --yes
```
Expected: confirmation that the repo was renamed.

- [ ] **Step 5: Update the local git remote to the new URL**

Run:
```bash
git remote set-url origin git@github.com:sublimecoder/claude-code-prompts-for-senior-engineers.git
git remote -v
```
Expected: both fetch/push lines show the new slug.

- [ ] **Step 6: Push all the content commits**

Run: `git push origin main`
Expected: pushes Tasks 1-10 commits without error.

---

## Task 12: Final verification pass

**Files:** none (read-only checks).

- [ ] **Step 1: Confirm every prompt H1 carries an exact-match query phrase**

Run:
```bash
cd /Users/jsmith/code/sublimecoding-marketing
grep -L -E '^# (Claude Code|AI Code Review)' prompts/*.md | grep -v 'README.md'
```
Expected: NO output (every prompt file's H1 starts with "Claude Code" or "AI Code Review"; an empty result means all pass).

- [ ] **Step 2: Confirm no bare (un-tagged) vault/consulting links remain in prompt files**

Run:
```bash
grep -rEn 'sublimecoding\.com/(vault|consulting)\)' prompts/*.md | grep -v 'utm_' || echo "ALL TAGGED"
```
Expected: `ALL TAGGED` (no un-tagged outbound conversion links).

- [ ] **Step 3: Confirm new assets are tracked by git**

Run: `git ls-files cursorrules/ AGENTS.md`
Expected: both `cursorrules/senior-engineer.cursorrules` and `AGENTS.md` listed.

- [ ] **Step 4: Capture the measurement baseline** — record current Google rank (or "not ranking") for the target queries so progress is measurable at 4 and 8 weeks. Create `docs/seo-baseline-2026-06-23.md`:

```markdown
# SEO baseline — 2026-06-23

Manual rank check (incognito, google.com) for the renamed repo + key files.
Re-check at 2026-07-21 (4wk) and 2026-08-18 (8wk).

| Query | Rank 2026-06-23 | Rank +4wk | Rank +8wk |
|---|---|---|---|
| cursor prompts senior engineer | | | |
| best claude code prompts | | | |
| claude code security review prompt | | | |
| claude code production debugging prompt | | | |
| claude code prompt library | | | |
| CLAUDE.md template | | | |
| ai code review prompt | | | |
| cursor rules for senior engineers | | | |
| AGENTS.md template | | | |
```
Then run the checks manually and fill the first column.

- [ ] **Step 5: Commit the baseline**

```bash
git add docs/seo-baseline-2026-06-23.md
git commit -m "seo: capture rank baseline for target queries"
git push origin main
```

---

## Future work (not in this plan)
- `cursorrules/go-microservices.cursorrules`, `elixir.cursorrules`, `security.cursorrules` (Cluster B language/role spokes).
- Phase-2 site blog content feeder (6 posts) — separate coordinated spec touching the Phoenix site repo.
- Social-preview OG image (W1 item 4) — design asset, produce separately then set via repo Settings → Social preview.
```
