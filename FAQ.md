# FAQ — The Senior Engineer's AI Prompt Vault

Honest answers to what people actually ask about [the Vault](https://sublimecoding.com/vault).

If your question isn't here, email **jared@sublimecoding.com** — I read every one.

---

## Wait — it's free? What's the catch?

No catch. The Vault is free: 50 prompts, 5 `.cursorrules` files, 3 `CLAUDE.md` starters, and the Notion blueprint. No login, no expiry, no drip.

It used to be a paid pack. I made it free because free prompt collections are everywhere, and the honest play is to make the best one the front door — not to fight for $39 against a thousand giveaways. If the prompts earn your trust, you'll know where to find me for [the harder problems](https://sublimecoding.com/consulting).

## Is it actually any good?

If one prompt saves you a single production bug, or one "wait, why did Claude refactor that?" hour, it's done its job. That's the bar every prompt in here is built to clear.

If you only use Claude or Cursor occasionally, or you're happy with the answers you already get — you may not need it. I'd rather you skip it than download something you won't use.

## How is this different from the free prompt collections all over GitHub?

Two things:

1. **Audience.** Most public prompt collections are written for "anyone who codes." The Vault is written for staff/senior engineers shipping production systems — the prompts assume you already know what idempotency, blast radius, and characterization tests are, and they're tuned to enforce that level of rigor on the model.
2. **Failure-mode discipline.** Every prompt is structured around the specific way Claude / Cursor *fails* at that task — pattern-matching a fix before the root cause, extracting along line boundaries instead of intent, narrating diffs instead of helping the reviewer. Generic prompts don't fight those failure modes.

You can judge for yourself: [15 of them are right here in this repo](./prompts), no email required.

## Will these work in Cursor? Codex? Aider? Windsurf?

Yes. The prompts are tool-agnostic — they're system-prompt / chat-message text. I personally use them in Claude Code and Cursor daily, and I've validated them in Codex and Aider.

The 5 `.cursorrules` files are obviously Cursor-specific. The 3 `CLAUDE.md` starters are Claude-Code-specific in name but work as `AGENTS.md`, `.windsurfrules`, or any other "rules file" the tool reads — same content, different filename.

## Does it work for languages other than Go and Elixir?

The 50 prompts are language-agnostic — they're about *how to think*, not syntax. They work for any language Claude / Cursor know well (Python, TypeScript, Ruby, Rust, Java, Kotlin, Swift, etc.).

The 3 `CLAUDE.md` starters cover Go services, Elixir umbrellas, and AI-agent projects specifically because that's what I have direct production experience with and could write honestly about. If you need a Python or TypeScript starter, the structure of the Go one is directly portable — most people fork and adapt in 15 minutes.

## What does "lifetime updates" actually mean?

When I add new prompts, refine existing ones, or update starters for a new Claude/Cursor version, you get them. Forever. No re-download nag, no subscription.

I add to the Vault roughly monthly. Recent drops: a security review prompt, a "is this PR safe to revert?" prompt, and an Ecto migration safety prompt.

## Will the next version of Claude make these obsolete?

Possibly the boilerplate ones. Not the staff-engineer-level ones — those encode *what to ask the model to think about*, which is the part that doesn't get cheaper as models get better. The Claude 3.5 → 4 → 4.7 transition didn't obsolete a single prompt in the Vault. If anything, the better the model gets, the more leverage a well-structured prompt provides.

Either way: lifetime updates. If a model change breaks something, I update it.

## What's in the Notion blueprint?

A copy-to-your-workspace Notion database with all 50 prompts, organized three ways:

- By **category** (code review, debugging, refactoring, system design, docs)
- By **tool** (works in Claude Code, Cursor, Codex, generic)
- By **frequency** (daily / weekly / situational)

Plus a "how I'm using this today" log so you can track which prompts you actually reach for. Fork it, share it within your team, or keep it private — your workspace.

## Can I use these at work? Share them with my team?

Yes — personal and commercial use, no restrictions. Use the prompts in your day job, share the `.cursorrules` and `CLAUDE.md` files with your team, check them into your company repos. The only thing not allowed is repackaging the Vault and reselling it as your own.

## Who's the author? Why should I trust this?

Jared Smith. 13+ years shipping production software. Currently Director of Information Security at Lavender. Backend at BlockFi, Elixir at AAMP Global, co-founded a startup and scaled engineering from 1 to 15. Daily Claude / Cursor / Codex user since 2023.

The prompts came from the actual problem of "I have to teach 14 other engineers how to use AI without it making their code worse" — that's where the failure-mode framing comes from.

More background: [sublimecoding.com](https://sublimecoding.com) · [@sublimecoder on X](https://x.com/sublimecoder) · [LinkedIn](https://www.linkedin.com/in/jared-smith-ab834565/).

## Will you write more prompts?

Yes, roughly monthly drops. Recent additions: a security review prompt, a "is this PR safe to revert?" prompt, and an Ecto migration safety prompt.

If there's a category you wish the Vault covered better, email me — requests jump the queue.

---

## Ready?

Free · lifetime updates · no app, no login.

→ **[Get the Vault](https://sublimecoding.com/vault)**

Or [try the 15 free sample prompts](./prompts) right here first.
