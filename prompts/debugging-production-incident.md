# Debugging — Production Incident: First 10 Minutes

A staff-level Debugging prompt for Claude Code, Cursor, and other AI coding assistants.

**Use it when:** Page just fired. You're alone. What now.

**Why it works:** Under pressure, even senior engineers skip steps. A short, specific runbook generated for the alert in front of you beats a generic IR doc.

---

```
I just got paged. Walk me through the first 10 minutes.

Alert:
<paste alert text>

What I see in dashboards:
<quick description>

Generate, in this exact order:
1. The 60-second triage checklist. (Is this real? What's the user impact? Anyone else aware?)
2. The 3 most likely causes given the alert and recent history.
3. The single mitigation I should attempt first (revert, rollback, scale up, kill the bad pod, traffic shift).
4. The communication template: who to notify, in what channel, with what context.
5. What to capture for the postmortem before it gets cleaned up.

Be terse. I'm under pressure.
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
