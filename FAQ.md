# FAQ — The Senior Engineer's AI Prompt Vault

Honest answers to what people actually ask before buying [the Vault](https://sublimecoding.com/vault).

If your question isn't here, email **jared@sublimecoding.com** — I read every one.

---

## Is the Vault actually worth $39?

If one prompt saves you one production bug or one wasted hour of "wait, why did Claude refactor that?" it's paid for itself. Most buyers report that within the first week.

If you only use Claude or Cursor occasionally, or you're happy with the answers you're already getting — probably not for you. I'd rather you skip it than ask for a refund.

## Why $39 and not free?

Free prompts exist. I have [5 of mine free](./prompts) and I link to other people's collections in [the Claude Code Resource Bible](https://sublimecoding.com/blog/claude-code-resource-bible).

The Vault is the curated, tested set I actually use — refined across 100K+ users of live AI products, an InfoSec leadership role, and three years of daily Claude / Cursor / Codex work. The $39 buys curation and the fact that I keep maintaining it.

The founders price ($39 for the first 50 buyers, then $49) exists because I'd rather have honest early feedback than a marketing campaign.

## How is this different from free prompt collections on GitHub?

Two things:

1. **Audience.** Most public prompt collections are written for "anyone who codes." The Vault is written for staff/senior engineers shipping production systems — the prompts assume you already know what idempotency, blast radius, and characterization tests are, and they're tuned to enforce that level of rigor on the model.
2. **Failure-mode discipline.** Every prompt is structured around the specific way Claude / Cursor *fails* at that task — pattern-matching a fix before the root cause, extracting along line boundaries instead of intent, narrating diffs instead of helping the reviewer. Generic prompts don't fight those failure modes.

That said: if a free collection is solving your problem, use it. The Vault is for people who've already tried the free stuff and still aren't happy with the answers.

## Will these work in Cursor? Codex? Aider? Windsurf?

Yes. The prompts are tool-agnostic — they're system-prompt / chat-message text. I personally use them in Claude Code and Cursor daily, and I've validated them in Codex and Aider.

The 5 `.cursorrules` files are obviously Cursor-specific. The 3 `CLAUDE.md` starters are Claude-Code-specific in name but work as `AGENTS.md`, `.windsurfrules`, or any other "rules file" the tool reads — same content, different filename.

## Does it work for languages other than Go and Elixir?

The 50 prompts are language-agnostic — they're about *how to think*, not syntax. They work for any language Claude / Cursor know well (Python, TypeScript, Ruby, Rust, Java, Kotlin, Swift, etc.).

The 3 `CLAUDE.md` starters cover Go services, Elixir umbrellas, and AI-agent projects specifically because that's what I have direct production experience with and could write honestly about. If you need a Python or TypeScript starter, the structure of the Go one is directly portable — most buyers fork and adapt in 15 minutes.

## What does "lifetime updates" actually mean?

When I add new prompts, refine existing ones, or update starters for a new Claude/Cursor version, you get them. Forever. No re-buy, no subscription.

I add to the Vault roughly monthly. Recent buyers got 7 new prompts and updated `.cursorrules` files in the last drop.

## What if I don't like it?

7-day refund, no questions. Email me, I send the money back, you keep everything. If something didn't click for you I'd rather know what and fix it than have you stew.

## Will the next version of Claude make these obsolete?

Possibly the boilerplate ones. Not the staff-engineer-level ones — those encode *what to ask the model to think about*, which is the part that doesn't get cheaper as models get better. The Claude 3.5 → 4 → 4.7 transition didn't obsolete a single prompt in the Vault. If anything, the better the model gets, the more leverage a well-structured prompt provides.

Either way: lifetime updates. If a model change breaks something, I update it.

## What's in the Notion blueprint?

A copy-to-your-workspace Notion database with all 50 prompts, organized three ways:

- By **category** (code review, debugging, refactoring, system design, docs)
- By **tool** (works in Claude Code, Cursor, Codex, generic)
- By **frequency** (daily / weekly / situational)

Plus a "how I'm using this today" log so you can track which prompts you actually reach for. You can fork it, share it within your team, or keep it private — your workspace.

## Can I use these at work? Commercial license?

Yes. The Vault is licensed for personal *and* commercial use. You can use the prompts in your day job, share the `.cursorrules` and `CLAUDE.md` files with your team, and check them into your company repos. The only thing you can't do is resell the Vault itself or redistribute it publicly.

If your company wants a team license for 10+ engineers with a shared Notion workspace, email me — I have a team rate.

## Who's the author? Why should I trust this?

Jared Smith. 13+ years shipping production software. Currently Director of Information Security at Lavender. Backend at BlockFi, Elixir at AAMP Global, co-founded a startup and scaled engineering from 1 to 15. Daily Claude / Cursor / Codex user since 2023.

The prompts came from the actual problem of "I have to teach 14 other engineers how to use AI without it making their code worse" — that's where the failure-mode framing comes from.

More background: [sublimecoding.com](https://sublimecoding.com) · [@sublimecoder on X](https://x.com/sublimecoder) · [LinkedIn](https://www.linkedin.com/in/jared-smith-ab834565/).

## Will you write more prompts?

Yes, roughly monthly drops. Recent additions: a security review prompt, a "is this PR safe to revert?" prompt, and an Ecto migration safety prompt. Buyers get them all automatically.

If there's a category you wish the Vault covered better, email me — buyer requests jump the queue.

---

## Ready?

**$39 founders edition** (first 50 buyers, then $49) · 7-day refund · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

Still on the fence? [Try the 5 free sample prompts](./prompts) first.
