# Phase 2 Blog Content-Feeder Briefs Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Produce 6 SERP-informed content briefs (one Markdown file each) in the site repo at `../sublimecoding-site/docs/content-briefs/`, each a complete writing kit Jared can write prose against.

**Architecture:** Briefs are content artifacts, not code. Each brief task: (1) does fresh live-SERP recon via WebSearch/WebFetch, (2) checks the site's existing posts for cannibalization, (3) fills a shared 9-section template, (4) passes a structural verification (all 9 sections, valid frontmatter, ≥2 cited source URLs), (5) commits. The shared template is created once (Task 1) and copied per brief (DRY). All file creation and commits happen in the SITE repo (`../sublimecoding-site`), not this marketing repo.

**Tech Stack:** Markdown, YAML frontmatter, `git`, `grep`, WebSearch/WebFetch (recon). No app code touched.

**Spec:** `docs/superpowers/specs/2026-06-23-phase2-blog-content-feeder-design.md` (in this marketing repo).

**Cross-repo:** Implementers work in `/Users/jsmith/code/sublimecoding-site`. Brief files go under `docs/content-briefs/` there (a non-served dir — never published).

**"Real recon" enforcement:** Every brief MUST cite the actual URLs it analyzed in a `**Sources:**` line inside Section 2 and/or 3. Verification greps for ≥2 `http` URLs. Fabricated briefs without sources fail the gate.

---

## File map (all in `../sublimecoding-site/`)

| File | Action | Responsibility |
|---|---|---|
| `docs/content-briefs/_TEMPLATE.md` | Create (Task 1) | Shared 9-section brief skeleton |
| `docs/content-briefs/README.md` | Create (Task 1), finalize (Task 8) | Index of the 6 briefs + status |
| `docs/content-briefs/prompt-injection-claude-code-cicd.md` | Create (Task 2) | Brief #1 |
| `docs/content-briefs/claude-md-vs-agents-md.md` | Create (Task 3) | Brief #2 |
| `docs/content-briefs/ai-coding-workflow-staff-engineer.md` | Create (Task 4) | Brief #3 |
| `docs/content-briefs/cursor-vs-claude-code-backend.md` | Create (Task 5) | Brief #4 |
| `docs/content-briefs/cursorrules-vs-claude-md.md` | Create (Task 6) | Brief #5 |
| `docs/content-briefs/how-to-write-claude-md-production.md` | Create (Task 7) | Brief #6 |

**Shared reference data** (used by Tasks 2–7):
- Repo prompt files live at `https://github.com/sublimecoder/sublimecoding/blob/main/prompts/<file>.md`
- Repo extras: `.../blob/main/cursorrules/senior-engineer.cursorrules`, `.../blob/main/AGENTS.md`
- External CLAUDE.md starter repos: `github.com/sublimecoder/claude-md-go-starter`, `…/claude-md-elixir-starter`, `…/claude-md-ai-agents-starter`
- Vault CTA: `https://sublimecoding.com/vault?utm_source=blog&utm_medium=post&utm_campaign=vault`
- Consulting CTA: `https://sublimecoding.com/consulting?utm_source=blog&utm_medium=post&utm_campaign=consulting`
- Existing tag taxonomy (reuse, no new tags): `Elixir, AI, engineering, founders, engineering leadership, AI tools, agents, productivity, Phoenix, developer workflows, AI startups, claude code, security, staff engineer, go`

---

## Task 1: Scaffold the briefs directory, shared template, and index

**Files (site repo):**
- Create: `docs/content-briefs/_TEMPLATE.md`
- Create: `docs/content-briefs/README.md`

- [ ] **Step 1: Confirm the site repo and create a working branch**

Run:
```bash
cd /Users/jsmith/code/sublimecoding-site
git rev-parse --is-inside-work-tree && git checkout -b phase2-content-briefs && mkdir -p docs/content-briefs && echo OK
```
Expected: prints `true`, switches to new branch `phase2-content-briefs`, prints `OK`.

- [ ] **Step 2: Create the shared template** `docs/content-briefs/_TEMPLATE.md` with this exact content:

```markdown
# Brief: <Working Title>

**Status:** todo
**Primary query:** <query>
**Funnel target:** <Vault | Consulting | both>
**Assigned publishDate:** <YYYY-MM-DDT14:00:00Z>

## 1. Targets
- **Primary:** <primary query>
- **Secondary:** <2–3 secondary / long-tail queries>

## 2. Intent & SERP Angle
<Search intent. What currently ranks and why it's weak. Our specific wedge.>
**Sources:** <list the actual result URLs analyzed — at least 2>

## 3. Competitor H2 Map + Gaps
<The H2 structure of the top ranking pages, and the gaps we exploit.>

## 4. People Also Ask
<PAA / related questions the post must answer. Each maps to a section or FAQ entry.>

## 5. Frontmatter (paste-ready)
```yaml
---
title: "<title>"
slug: "<slug>"
description: "<meta description, ≤155 chars>"
publishDate: "<YYYY-MM-DDT14:00:00Z>"
updatedDate: "<same as publishDate>"
author: "Jared Smith"
tags: [<from existing taxonomy>]
canonical: "https://sublimecoding.com/blog/<slug>"
readingTime: "<N> min"
---
```

## 6. Outline (section → word target → angle/proof)
<H2/H3 outline. Per-section word-count target. The proof/angle each section carries. Total target derived from what ranks.>

## 7. E-E-A-T Hooks
<Exact places to anchor Jared's first-person production experience: named systems, scale numbers, real incidents.>

## 8. Interlink Map
- **Repo files (download CTA):** <which repo files/links>
- **Existing site posts to link:** <slugs>
- **Existing posts to add a back-link to this one:** <slugs>
- **CTA placement & anchor text:** <Vault vs Consulting, where>

## 9. Cannibalization Note
<Overlap decision vs named existing posts and the chosen wedge.>
```

- [ ] **Step 3: Create the index** `docs/content-briefs/README.md` with this exact content:

```markdown
# Content Briefs — Phase 2 Blog Feeder

SERP-informed briefs for the 6 comparison/explainer/how-to posts that feed sublimecoding.com.
Each is a writing kit — Jared writes the prose into `content/posts/<slug>.md`.
Spec: `sublimecoding-marketing/docs/superpowers/specs/2026-06-23-phase2-blog-content-feeder-design.md`.

| # | Brief | Primary query | publishDate | Status |
|---|---|---|---|---|
| 1 | [prompt-injection-claude-code-cicd](./prompt-injection-claude-code-cicd.md) | prompt injection claude code ci/cd | 2026-06-24 | todo |
| 2 | [claude-md-vs-agents-md](./claude-md-vs-agents-md.md) | claude.md vs agents.md | 2026-06-26 | todo |
| 3 | [ai-coding-workflow-staff-engineer](./ai-coding-workflow-staff-engineer.md) | ai coding workflow staff engineer | 2026-06-29 | todo |
| 4 | [cursor-vs-claude-code-backend](./cursor-vs-claude-code-backend.md) | cursor vs claude code backend | 2026-07-01 | todo |
| 5 | [cursorrules-vs-claude-md](./cursorrules-vs-claude-md.md) | .cursorrules vs claude.md | 2026-07-03 | todo |
| 6 | [how-to-write-claude-md-production](./how-to-write-claude-md-production.md) | how to write claude.md | 2026-07-06 | todo |
```

- [ ] **Step 4: Verify scaffold**

Run:
```bash
cd /Users/jsmith/code/sublimecoding-site
test -f docs/content-briefs/_TEMPLATE.md && grep -c '^## [1-9]\.' docs/content-briefs/_TEMPLATE.md && grep -c '^| [1-6] |' docs/content-briefs/README.md
```
Expected: `9` (nine numbered sections in the template) then `6` (six brief rows in the index).

- [ ] **Step 5: Commit**

```bash
cd /Users/jsmith/code/sublimecoding-site
git add docs/content-briefs/_TEMPLATE.md docs/content-briefs/README.md
git commit -m "content-briefs: scaffold template + index for Phase 2 blog feeder"
```

---

## Brief tasks — shared procedure (applies to Tasks 2–7)

Each brief task follows the SAME procedure; only the per-post parameters differ.

1. Copy the template: `cp docs/content-briefs/_TEMPLATE.md docs/content-briefs/<slug>.md`
2. **Fresh SERP recon:** run the task's listed WebSearch queries; open (WebFetch) the top 3–5 ranking results; record their H2 headings, the People-Also-Ask / related questions, and the approximate word count of the best result. Capture the actual URLs.
3. **Cannibalization check:** read the named existing posts in `../sublimecoding-site/content/posts/` and decide the wedge per the task.
4. **Fill every template section** with real findings. Replace ALL `<…>` markers. Section 2 and/or 3 MUST include a `**Sources:**` line with the real URLs analyzed (≥2). Use only tags from the existing taxonomy. Set `publishDate`/`updatedDate`/`canonical`/`slug`/`title` to the task's values. Set `**Status:** drafted`.
5. **Verify** (structural gate):
```bash
cd /Users/jsmith/code/sublimecoding-site
F=docs/content-briefs/<slug>.md
echo "sections: $(grep -c '^## [1-9]\.' $F)"      # expect 9
echo "frontmatter: $(grep -c '^canonical:' $F)"    # expect 1
echo "sources: $(grep -c 'http' $F)"               # expect >= 2
echo "unfilled markers: $(grep -c '<[a-z]' $F)"    # expect 0
```
Expected: `sections: 9`, `frontmatter: 1`, `sources >= 2`, `unfilled markers: 0`. (The marker check is a heuristic — if a brief legitimately contains `<word>` in prose/code, eyeball it rather than blindly "fixing".)
6. **Commit:** `git add docs/content-briefs/<slug>.md && git commit -m "content-briefs: <slug> (SERP-informed)"`

If a verification line fails, fix the brief before committing. If live SERP recon returns nothing usable for a query, report DONE_WITH_CONCERNS noting which query was thin — do not fabricate sources.

---

## Task 2: Brief #1 — Prompt injection risks in Claude Code CI/CD

**Files (site repo):** Create `docs/content-briefs/prompt-injection-claude-code-cicd.md`

Follow the shared procedure with these parameters:
- **Working title:** "Prompt Injection Risks in Claude Code CI/CD (and How to Contain Them)"
- **slug:** `prompt-injection-claude-code-cicd` · **canonical:** `https://sublimecoding.com/blog/prompt-injection-claude-code-cicd`
- **publishDate:** `2026-06-24T14:00:00Z` · **Funnel target:** Consulting (security)
- **Primary query:** `prompt injection claude code ci/cd`. **Secondaries:** `claude code security risks`, `ai coding agent prompt injection`, `securing ai agents in ci`
- **Suggested tags:** `security, AI tools, agents, AI startups`
- **WebSearch queries to run:** `prompt injection claude code`, `prompt injection ai coding agent ci/cd`, `claude code security best practices`, `ai agent prompt injection mitigation`
- **Cannibalization:** distinct from `enterprise-security-reviews-ai-startups` and `surviving-technical-due-diligence-ai-founder` (those are due-diligence/review focused). Interlink, don't compete.
- **Repo files for download CTA:** `prompts/code-review-security-first.md`, `cursorrules/senior-engineer.cursorrules`, `AGENTS.md`
- **E-E-A-T angle:** Director of Information Security; production AI guardrails; real CI/CD exposure.

- [ ] **Step 1:** Copy template, run recon, check cannibalization, fill all sections (per shared procedure steps 1–4).
- [ ] **Step 2:** Run the verification block (shared procedure step 5). Expected: `sections: 9`, `frontmatter: 1`, `http >= 2`, `unfilled markers: 0`.
- [ ] **Step 3:** Commit (shared procedure step 6).

---

## Task 3: Brief #2 — CLAUDE.md vs AGENTS.md

**Files (site repo):** Create `docs/content-briefs/claude-md-vs-agents-md.md`

Follow the shared procedure with these parameters:
- **Working title:** "CLAUDE.md vs AGENTS.md: What a Staff Engineer Actually Uses"
- **slug:** `claude-md-vs-agents-md` · **canonical:** `https://sublimecoding.com/blog/claude-md-vs-agents-md`
- **publishDate:** `2026-06-26T14:00:00Z` · **Funnel target:** Vault (CLAUDE.md starters)
- **Primary query:** `claude.md vs agents.md`. **Secondaries:** `agents.md vs claude.md`, `claude code instructions file`, `agents.md format`
- **Suggested tags:** `AI tools, agents, developer workflows, claude code`
- **WebSearch queries to run:** `CLAUDE.md vs AGENTS.md`, `AGENTS.md vs CLAUDE.md staff engineer`, `agents.md specification`, `claude.md best practices`
- **Cannibalization:** overlaps `claude-md-after-50-commits` (personal/mistake-driven). Wedge: this is the comparison/decision post; cross-link to the retrospective. Add a reciprocal back-link note.
- **Repo files for download CTA:** `AGENTS.md`, the 3 external CLAUDE.md starter repos, `prompts/` index.
- **E-E-A-T angle:** which file he checks in across Go/Elixir prod repos and why.

- [ ] **Step 1:** Copy template, run recon, check cannibalization, fill all sections.
- [ ] **Step 2:** Run the verification block. Expected: `sections: 9`, `frontmatter: 1`, `http >= 2`, `unfilled markers: 0`.
- [ ] **Step 3:** Commit.

---

## Task 4: Brief #3 — The AI coding workflow of a staff engineer

**Files (site repo):** Create `docs/content-briefs/ai-coding-workflow-staff-engineer.md`

Follow the shared procedure with these parameters:
- **Working title:** "The AI Coding Workflow of a Staff Engineer"
- **slug:** `ai-coding-workflow-staff-engineer` · **canonical:** `https://sublimecoding.com/blog/ai-coding-workflow-staff-engineer`
- **publishDate:** `2026-06-29T14:00:00Z` · **Funnel target:** Vault (all 15 prompts)
- **Primary query:** `ai coding workflow staff engineer`. **Secondaries:** `how senior engineers use ai`, `claude code workflow`, `ai pair programming senior engineer`
- **Suggested tags:** `AI tools, developer workflows, staff engineer, productivity`
- **WebSearch queries to run:** `ai coding workflow senior engineer`, `how staff engineers use claude code`, `ai pair programming workflow`, `claude code daily workflow`
- **Cannibalization:** distinct from `things-ai-coding-agents-get-wrong`, `stop-making-senior-engineers`, `professional-owns-the-outcome` — supporting cluster; interlink all three.
- **Repo files for download CTA:** link to the full `prompts/` library (all 15) and `cursorrules/senior-engineer.cursorrules`.
- **E-E-A-T angle:** his actual loop teaching 14 engineers; named tools (Claude Code, Cursor, Codex since 2023).

- [ ] **Step 1:** Copy template, run recon, check cannibalization, fill all sections.
- [ ] **Step 2:** Run the verification block. Expected: `sections: 9`, `frontmatter: 1`, `http >= 2`, `unfilled markers: 0`.
- [ ] **Step 3:** Commit.

---

## Task 5: Brief #4 — Cursor vs Claude Code for backend engineers

**Files (site repo):** Create `docs/content-briefs/cursor-vs-claude-code-backend.md`

Follow the shared procedure with these parameters:
- **Working title:** "Cursor vs Claude Code for Backend Engineers"
- **slug:** `cursor-vs-claude-code-backend` · **canonical:** `https://sublimecoding.com/blog/cursor-vs-claude-code-backend`
- **publishDate:** `2026-07-01T14:00:00Z` · **Funnel target:** Vault + Consulting
- **Primary query:** `cursor vs claude code backend`. **Secondaries:** `cursor vs claude code`, `best ai coding tool backend`, `claude code or cursor for go/elixir`
- **Suggested tags:** `AI tools, developer workflows, claude code, engineering`
- **WebSearch queries to run:** `cursor vs claude code`, `cursor vs claude code backend engineer`, `claude code vs cursor 2026`, `best ai coding assistant for backend`
- **Cannibalization:** distinct from `claude-code-resource-bible` and `ruflo-claude-flow-multi-agent-deep-dive`; interlink as deeper tooling context.
- **Repo files for download CTA:** `cursorrules/senior-engineer.cursorrules`, `prompts/` index.
- **E-E-A-T angle:** the call his team made for Go/Elixir backend work and why; distributed-systems lens.

- [ ] **Step 1:** Copy template, run recon, check cannibalization, fill all sections.
- [ ] **Step 2:** Run the verification block. Expected: `sections: 9`, `frontmatter: 1`, `http >= 2`, `unfilled markers: 0`.
- [ ] **Step 3:** Commit.

---

## Task 6: Brief #5 — .cursorrules vs CLAUDE.md

**Files (site repo):** Create `docs/content-briefs/cursorrules-vs-claude-md.md`

Follow the shared procedure with these parameters:
- **Working title:** ".cursorrules vs CLAUDE.md: Which to Check Into Your Repo"
- **slug:** `cursorrules-vs-claude-md` · **canonical:** `https://sublimecoding.com/blog/cursorrules-vs-claude-md`
- **publishDate:** `2026-07-03T14:00:00Z` · **Funnel target:** Vault (.cursorrules)
- **Primary query:** `.cursorrules vs claude.md`. **Secondaries:** `cursorrules vs claude md`, `which ai rules file to commit`, `cursorrules and claude.md together`
- **Suggested tags:** `AI tools, developer workflows, claude code`
- **WebSearch queries to run:** `.cursorrules vs CLAUDE.md`, `cursorrules vs claude.md which to use`, `commit cursorrules to repo`, `cursor rules vs claude code instructions`
- **Cannibalization:** overlaps `claude-md-after-50-commits` lightly; wedge is the head-to-head "which to commit" decision. Cross-link.
- **Repo files for download CTA:** `cursorrules/senior-engineer.cursorrules`, `AGENTS.md`, the 3 CLAUDE.md starter repos.
- **E-E-A-T angle:** what he actually checks in on team repos and the rationale.

- [ ] **Step 1:** Copy template, run recon, check cannibalization, fill all sections.
- [ ] **Step 2:** Run the verification block. Expected: `sections: 9`, `frontmatter: 1`, `http >= 2`, `unfilled markers: 0`.
- [ ] **Step 3:** Commit.

---

## Task 7: Brief #6 — How to write a CLAUDE.md that works in production

**Files (site repo):** Create `docs/content-briefs/how-to-write-claude-md-production.md`

Follow the shared procedure with these parameters:
- **Working title:** "How to Write a CLAUDE.md That Works in Production"
- **slug:** `how-to-write-claude-md-production` · **canonical:** `https://sublimecoding.com/blog/how-to-write-claude-md-production`
- **publishDate:** `2026-07-06T14:00:00Z` · **Funnel target:** Vault (CLAUDE.md starters)
- **Primary query:** `how to write claude.md`. **Secondaries:** `claude.md best practices`, `claude.md template production`, `claude code configuration guide`
- **Suggested tags:** `AI tools, developer workflows, claude code, productivity`
- **WebSearch queries to run:** `how to write CLAUDE.md`, `claude.md best practices production`, `claude.md template guide`, `writing a good claude.md`
- **Cannibalization (CONFIRMED reframe):** this is the how-to/guide; `claude-md-after-50-commits` is the personal retrospective. They MUST target different intents. The brief's Section 9 states the explicit split and adds a reciprocal cross-link (this post → retrospective for "what I learned"; retrospective → this post for "the how-to"). Do NOT fold in.
- **Repo files for download CTA:** the 3 external CLAUDE.md starter repos, `AGENTS.md`.
- **E-E-A-T angle:** the structure that survived 50+ commits on a real project.

- [ ] **Step 1:** Copy template, run recon, check cannibalization, fill all sections.
- [ ] **Step 2:** Run the verification block. Expected: `sections: 9`, `frontmatter: 1`, `http >= 2`, `unfilled markers: 0`.
- [ ] **Step 3:** Commit.

---

## Task 8: Finalize the index and run cross-brief verification

**Files (site repo):** Modify `docs/content-briefs/README.md`

- [ ] **Step 1: Flip all 6 statuses to `done` in the index**

Run:
```bash
cd /Users/jsmith/code/sublimecoding-site
sed -i '' 's/| todo |/| done |/g' docs/content-briefs/README.md
grep -c '| done |' docs/content-briefs/README.md
```
Expected: `6`.

- [ ] **Step 2: Verify all 6 briefs exist, each fully filled, no unfilled markers anywhere**

Run:
```bash
cd /Users/jsmith/code/sublimecoding-site
ls docs/content-briefs/*.md | grep -vE '_TEMPLATE|README' | wc -l    # expect 6
echo "section completeness:"
for f in docs/content-briefs/*.md; do
  case "$f" in *_TEMPLATE*|*README*) continue;; esac
  printf "%s: sections=%s markers=%s sources=%s\n" "$(basename $f)" \
    "$(grep -c '^## [1-9]\.' $f)" "$(grep -c '<[a-z]' $f)" "$(grep -c 'http' $f)"
done
```
Expected: `6`; then one line per brief with `sections=9 markers=0 sources>=2`.

- [ ] **Step 3: Confirm tag taxonomy compliance (no invented tags)**

Run:
```bash
cd /Users/jsmith/code/sublimecoding-site
grep -h '^tags:' docs/content-briefs/*.md 2>/dev/null
```
Expected: each `tags:` line uses only values from the existing taxonomy (Elixir, AI, engineering, founders, engineering leadership, AI tools, agents, productivity, Phoenix, developer workflows, AI startups, claude code, security, staff engineer, go). Manually confirm no new tag slipped in.

- [ ] **Step 4: Commit**

```bash
cd /Users/jsmith/code/sublimecoding-site
git add docs/content-briefs/README.md
git commit -m "content-briefs: mark all 6 Phase 2 briefs done"
```

---

## Done criteria
- 6 brief files + `_TEMPLATE.md` + `README.md` in `../sublimecoding-site/docs/content-briefs/`, on branch `phase2-content-briefs`.
- Each brief: 9 sections filled, valid frontmatter with assigned publishDate + canonical, ≥2 cited source URLs, zero unfilled `<…>` markers, taxonomy-compliant tags.
- Index shows all 6 `done`.
- Nothing under `content/posts/` or app code changed.

## Out of scope (per spec)
- Writing/publishing the actual posts.
- OG images.
- Go/Elixir/security `.cursorrules` spokes.
