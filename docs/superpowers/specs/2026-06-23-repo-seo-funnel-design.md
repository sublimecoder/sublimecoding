# Repo-as-SEO-Asset & Sales-Funnel Design

**Date:** 2026-06-23
**Repo:** `sublimecoding-marketing` (the public GitHub prompt repo)
**Goal:** Use this repo to drive SEO + the sales pipeline for `sublimecoding.com` (Vault → Consulting).
**Primary objective (user-selected):** SEO for the site, via all four mechanisms — rank the repo itself, brand/entity signals, content feeder, referral traffic.

---

## Strategy (one line)

Don't fight the 40k★ awesome-lists head-on. Turn this repo into an **exact-match-keyword, TOC-structured prompt library** that owns ~15 *under-defended* long-tail queries — each file funneling to `/vault` → `/consulting`. The **site blog** (phase 2) owns the comparison/explainer queries a GitHub repo can't win, linking back to repo files as the "download the prompt" CTA.

### Key constraint
GitHub outbound links are `nofollow` — this repo will **not** pass link authority to sublimecoding.com. Its real SEO jobs are: (1) rank the repo + its individual `.md` files, (2) throw off referral traffic + brand/entity signals, (3) feed content that ranks on the domain we own.

---

## Research findings (two independent SERP tracks, converging)

**Competitor landscape:**
- Exact-match keyword in the **repo NAME** is the strongest GitHub ranking signal. Current name carries none.
- Incumbents to avoid head-on: `PatrickJS/awesome-cursorrules` (~40k★, owns `.cursorrules`), `hesreallyhim/awesome-claude-code` (~47k★, owns `awesome claude code`).
- **Under-defended gaps (our targets):**
  - `cursor prompts senior engineer` — *no focused repo on page 1* (blogs + a Gist). Strongest opening.
  - `best claude code prompts` — only listicle blogspam.
  - `ai code review prompt` — leader ~134★ (beatable).
  - `CLAUDE.md template` — leader ~262★ (beatable).
  - `claude code prompt library` — no dominant focused repo.

**Keyword clusters:**
- **A — CLAUDE.md / AGENTS.md config files** (repo + standalone starters + blog comparisons).
- **B — `.cursorrules`** (head term owned by incumbent; *role/language modifiers are wide open*).
- **C — Prompt files by task type** (the repo's existing 15 files already fit — gap is titles/H1/first-160-chars).
- **D — cursor prompts** (README sections).

**Highest-ROI insight:** the repo already has the right 15 files. The gap is their **titles, H1s, and first ~160 characters** — what GitHub indexes and Google shows as the snippet. Fixing those needs *no new content*.

---

## Decisions locked

- **Repo rename:** YES — keyword slug, **keep the SublimeCoding brand** in About/README. GitHub 301-redirects the old URL, so existing stars/links/the 3 linked starter repos survive.
- **Recommended slug:** `claude-code-prompts-for-senior-engineers` (matches the most distinctive, winnable, high-funnel query verbatim). Alternative: `claude-cursor-prompts`. *Final slug to confirm at spec review.*
- **CLAUDE.md starters stay standalone repos** (`claude-md-go-starter`, etc.) — each ranks on its own exact-match name. This repo adds a "CLAUDE.md Templates" section that targets `CLAUDE.md template` and links out to them.

---

## Workstreams

### W1 — Repo positioning (biggest levers, near-zero content)
1. **Rename** repo to the confirmed keyword slug; keep "SublimeCoding" identity in README H1 subtitle + About.
2. **About description** — keyword-front-loaded, names both tools + audience + asset types. Draft:
   > 🛠️ Free Claude Code & Cursor prompts for senior engineers — code review, debugging, refactoring, system design, CLAUDE.md & .cursorrules templates. Plus a free Vault of 50 prompts.
3. **Topics/tags:** `claude-code`, `cursor`, `cursorrules`, `claude`, `anthropic`, `prompts`, `prompt-engineering`, `prompt-library`, `ai-code-review`, `code-review`, `claude-md`, `llm`, `agentic-coding`, `senior-engineer`, `go`, `elixir`.
4. **Social-preview OG image** — branded, for share/referral CTR.

### W2 — Optimize the 15 existing prompt files (no new content)
For each file: ensure the **H1 and first ~160 characters** contain the exact long-tail phrase a searcher types, plus "Claude Code / Cursor". Add a consistent per-file **CTA footer** → `/vault` + `/consulting`. Target queries (all near-zero competition, high funnel value):

| File | Target query |
|---|---|
| `code-review-security-first.md` | claude code security review prompt |
| `debugging-production-incident.md` | claude code production debugging prompt |
| `debugging-race-condition.md` | claude code race condition debugging prompt |
| `refactoring-god-class.md` | claude code god class refactoring prompt |
| `code-review-blast-radius.md` | ai code review prompt blast radius |
| `system-design-idempotency.md` | claude code idempotency design prompt |
| `system-design-rate-limiter.md` | claude code rate limiter design prompt |
| `docs-adr.md` | claude code ADR prompt |
| `docs-postmortem.md` | claude code postmortem prompt |
| `code-review-migration-safety.md` | claude code migration safety review prompt |
| `debugging-hypothesis-driven.md` | claude code debugging prompt |
| `refactoring-illegal-states.md` | claude code refactoring prompt (illegal states) |
| `refactoring-long-functions.md` | claude code refactoring long functions prompt |
| `system-design-pick-a-queue.md` | claude code system design prompt (queue) |
| `docs-pr-description.md` | claude code PR description prompt |

### W3 — New files for open long-tails
- `cursorrules/` directory — at minimum `senior-engineer.cursorrules`; then `go-microservices.cursorrules`, `elixir.cursorrules`, `security.cursorrules`. Opens the wide-open Cluster B role/language modifiers (`cursor rules for senior engineers`, `cursor rules for Go microservices`, `cursor rules staff engineer`).
- `AGENTS.md` starter (1–2 production-grade examples) — emerging, fast-growing query, thin competition.

### W4 — README rewrite
- Exact-match **H1** + keyword-rich one-line intro (keep brand subtitle).
- A **Contents TOC** (every ranking incumbent has one — signals depth to GitHub + Google).
- A **verbatim H2 per cluster**: "Claude Code Prompts", "Cursor Prompts for Senior Engineers", "AI Code Review Prompts", "CLAUDE.md Templates", ".cursorrules for Senior Engineers". Section headings rank as long-tail entry points.
- "Why this works" rationale near each prompt group (matches the pattern of the official library that ranks).
- **CTAs** to the Vault near the top AND in a footer; consulting CTA in footer.
- Preserve existing author/E-E-A-T block, featured writing, consulting section, blog-post-list automation.

### W5 — Phase 2: site blog content feeder (separate coordinated spec)
6 posts that own the comparison/explainer SERPs repos can't win, each linking to repo files as the "download the prompt" CTA:
1. `CLAUDE.md vs AGENTS.md: what a staff engineer actually uses`
2. `cursor vs claude code for backend engineers`
3. `.cursorrules vs CLAUDE.md: which to check into your repo`
4. `how to write a CLAUDE.md that works in production`
5. `prompt injection risks in claude code CI/CD` (security edge = linkbait)
6. `the AI coding workflow of a staff engineer`

**Cannibalization guard:** repo README targets `claude code prompt library` (navigational, repo-wins SERPs); blog targets `best claude code prompts for senior engineers` (commercial, blog-wins SERPs). Keep them distinct.

---

## Success criteria

- Repo renamed to keyword slug; About + 16 topics live; OG image set.
- All 15 prompt files have exact-match H1 + first-160-char snippet + CTA footer.
- `cursorrules/` (≥1 file) + AGENTS.md starter added; README links them.
- README rewritten with TOC + 5 verbatim H2 cluster sections + top/footer CTAs.
- Measurement baseline captured for the 15 target queries (rank check) + repo→site referral tracking.

## Measurement (proxy — Search Console can't see github.com)
- Manual/automated rank checks on the 15 target queries (baseline now, re-check at 4 + 8 weeks).
- Repo→site referral clicks (UTM tags on README/file CTAs).
- Star growth; Vault signups attributed to the repo (UTM).

## Out of scope (this spec)
- W5 blog posts (separate coordinated spec).
- Any change to the Phoenix site repo.
- Paid SEO tooling (DataForSEO) — research used free SERP analysis.

## Open items to confirm at review
1. Final repo slug (`claude-code-prompts-for-senior-engineers` vs `claude-cursor-prompts`).
2. How many W3 `cursorrules/` files for v1 (just `senior-engineer`, or all four).
3. Whether to add the AGENTS.md starter now or defer to phase 2.
