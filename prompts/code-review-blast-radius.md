# Code Review — Blast Radius

**Use when:** Before merging any non-trivial change, especially across module boundaries or near production data paths.

**Why it works:** Style nits are what linters are for. The job of a human (or AI) reviewer is to find the things that page someone at 3am. This prompt skips the bikeshed and forces the model to map the actual failure surface.

---

```
You're reviewing this diff before I merge it. Don't list style nits — I have linters for that.

Tell me the blast radius: what breaks, who pages, what data moves, and what I can't roll back.

Specifically:
1. Identify every external surface this touches: HTTP endpoints, queue consumers, scheduled jobs, database tables, IAM roles, env vars, feature flags.
2. For each surface, name the realistic failure modes and which downstream systems feel them first.
3. Flag anything that's not idempotent and explain why a retry could double-charge, double-send, or double-write.
4. Flag anything that requires a coordinated rollback (DB migration + code, API contract, cache shape) and tell me the rollback recipe.
5. End with a single line: "Safe to merge: yes / no / not until X." No hedging.

If you can't tell from the diff alone what's at risk, ask me for the file or context you need. Don't guess.

DIFF:
<paste diff here>
```

---

This is 1 of 50 prompts in [The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault).
