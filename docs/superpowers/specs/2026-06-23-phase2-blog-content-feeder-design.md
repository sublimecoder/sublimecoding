# Phase 2 — Blog Content Feeder Design (SERP-Informed Briefs)

**Date:** 2026-06-23
**Spec lives in:** `sublimecoding-marketing` (SEO command center)
**Briefs ship to:** `../sublimecoding-site/docs/content-briefs/<slug>.md` (co-located with the content they feed; NOT under the served `content/posts/` dir)
**Target site:** `../sublimecoding-site` (Phoenix, file-based blog at `content/posts/*.md`)
**Predecessor:** `2026-06-23-repo-seo-funnel-design.md` (W5 of that spec)

> **Cross-repo note:** This is the one piece of the SEO program whose deliverables land in the *site* repo, not the marketing repo. The implementation plan creates/commits brief files in `../sublimecoding-site`.

---

## Goal
Produce **6 SERP-informed content briefs** — one Markdown file each — that own the comparison/explainer/how-to queries a GitHub repo can't rank for, capturing the ranking value on the domain we own (sublimecoding.com) and funneling readers to `/vault` → `/consulting`. Each brief is a complete writing kit; **Jared writes the prose** (preserving the first-person staff-engineer E-E-A-T that is the competitive edge). This spec does NOT produce drafts or publish posts.

## Why briefs, not drafts
The research showed our wedge on these SERPs is authentic E-E-A-T / first-person production experience. AI-drafted prose flattens that voice and undercuts the only durable advantage. Briefs let the author move fast while keeping the voice real.

---

## Site authoring contract (discovered)
A published post is one Markdown file in `../sublimecoding-site/content/posts/<slug>.md` with this frontmatter (system auto-generates JSON-LD `BlogPosting`, breadcrumbs, tag pages, and IndexNow submission):
```yaml
---
title: "..."
slug: "..."
description: "..."            # used as meta description
publishDate: "YYYY-MM-DDThh:mm:ssZ"
updatedDate: "YYYY-MM-DDThh:mm:ssZ"
author: "Jared Smith"
tags: ["...", "..."]
canonical: "https://sublimecoding.com/blog/<slug>"
readingTime: "N min"
---
```
**Tag taxonomy to reuse** (existing, by frequency): `Elixir`, `AI`, `engineering`, `founders`, `engineering leadership`, `AI tools`, `agents`, `productivity`, `Phoenix`, `developer workflows`, `AI startups`, `claude code`, `security`, `staff engineer`, `go`. Briefs reuse these; no new tags unless a gap is unavoidable (flagged if so).

---

## The 6 posts (ordered by funnel value × winnability)

| # | Working title | Primary query | Funnel target | publishDate |
|---|---|---|---|---|
| 1 | Prompt injection risks in Claude Code CI/CD | `prompt injection claude code ci/cd` | Consulting (security) | 2026-06-24 |
| 2 | CLAUDE.md vs AGENTS.md: what a staff engineer actually uses | `claude.md vs agents.md` | Vault (CLAUDE.md starters) | 2026-06-26 |
| 3 | The AI coding workflow of a staff engineer | `ai coding workflow staff engineer` | Vault (all 15 prompts) | 2026-06-29 |
| 4 | Cursor vs Claude Code for backend engineers | `cursor vs claude code backend` | Vault + Consulting | 2026-07-01 |
| 5 | .cursorrules vs CLAUDE.md: which to check into your repo | `.cursorrules vs claude.md` | Vault (.cursorrules) | 2026-07-03 |
| 6 | How to write a CLAUDE.md that works in production | `how to write claude.md` | Vault (CLAUDE.md starters) | 2026-07-06 |

**publishDate assignment:** The existing blog runs a Tue/Thu cadence, booked through 2026-07-23 (taken: 06-23, 06-25, 06-30, 07-02, 07-07, 07-09, 07-14, 07-16, 07-21, 07-23). These 6 fill open off-cadence weekday slots in priority order, spaced ~2–3 days, with zero clashes. Use `T14:00:00Z` to match existing posts. Dates are a recommended default the author can shift; the brief's frontmatter carries the assigned date.

## Cannibalization guard (vs existing site posts)
Fresh recon for each brief MUST check the site's own existing posts and resolve overlap explicitly:
- **#6** overlaps `claude-md-after-50-commits` (personal/mistake-driven). **Confirmed:** reframe #6 as a distinct how-to/guide targeting `how to write claude.md` with a reciprocal cross-link to the existing post — do NOT fold in. Recon sharpens the exact wedge so the two posts target different intents (how-to/guide vs. personal retrospective).
- **#1** is distinct from `enterprise-security-reviews-ai-startups` (due-diligence focus) — interlink, don't compete.
- **#3** is distinct from `things-ai-coding-agents-get-wrong` and `stop-making-senior-engineers` — interlink as supporting cluster.
- Every brief lists which existing posts to interlink and which should add a link **back** to the new post.

---

## Brief structure (the deliverable — each `content-briefs/<slug>.md` contains all of these)
1. **Targets** — primary query + 2–3 secondary/long-tail queries.
2. **Intent & SERP angle** — search intent; what currently ranks (from fresh recon); why it's weak; our specific wedge.
3. **Competitor H2 map + gaps** — the heading structure of the top ranking pages and the gaps we exploit.
4. **People-Also-Ask** — the PAA / related questions the post must answer (each maps to a section or FAQ).
5. **Frontmatter block** — paste-ready: title, slug, description (meta), tags (from taxonomy), canonical, readingTime estimate, `publishDate` placeholder.
6. **Outline** — section-by-section H2/H3 with per-section word-count targets and the proof/angle each section carries; total word-count target derived from what ranks.
7. **E-E-A-T hooks** — explicit places to anchor Jared's first-person production experience (named systems, scale numbers, real incidents).
8. **Interlink map** — repo files to link as "download the prompt/template" CTA; existing site posts to link; existing posts that should add a link back; Vault vs Consulting CTA placement and anchor text.
9. **Cannibalization note** — overlap decision vs existing posts (per guard above).

---

## Architecture / where things live
- Briefs: `../sublimecoding-site/docs/content-briefs/<slug>.md` — in the **site** repo, co-located with the content they feed but outside the served `content/posts/` dir so they are never published. One brief = one file = one writing unit, independently understandable.
- Published posts (later, out of scope): `../sublimecoding-site/content/posts/<slug>.md`.
- A short `docs/content-briefs/README.md` (site repo) indexes the 6 briefs, their target queries, assigned publishDate, and status.

## Production approach (implementation shape — detailed in the plan)
One fresh-SERP-recon subagent per post (run in parallel; each uses WebSearch/WebFetch to capture ranking pages, their H2s, PAA, and word counts, and checks the site's existing posts for overlap) → structured findings → assembled into the brief template above. Recon must also confirm the working title/slug against actual SERP language.

---

## Success criteria
- 6 brief files in `../sublimecoding-site/docs/content-briefs/`, each containing all 9 structure elements with **real fresh-SERP data** (not generic guesses).
- Each brief's frontmatter uses the existing tag taxonomy, the assigned `publishDate`, and a valid canonical URL pattern.
- Each brief resolves its cannibalization decision explicitly and lists reciprocal interlinks.
- `docs/content-briefs/README.md` index present (site repo).
- Briefs are self-sufficient: Jared can write the post from the brief without further research.

## Out of scope
- Writing or publishing the actual posts (Jared writes prose; publishing is a later step).
- Any change to the site's **application code** or **served `content/posts/`** — Phase 2 only adds non-served brief files under `../sublimecoding-site/docs/content-briefs/`.
- The Go/Elixir/security `.cursorrules` spokes (separate follow-up from Phase 1).
- OG images for posts.

## Resolved decisions (from review)
1. **Brief location:** site repo, `docs/content-briefs/` (briefs ship where the content does).
2. **#6 cannibalization:** reframe + reciprocal cross-link (not fold-in).
3. **publishDates:** assigned to open off-cadence weekday slots over 2026-06-24 → 07-06 (see table); author may shift.
