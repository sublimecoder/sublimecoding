# Debugging — Hypothesis-Driven Root Cause

**Use when:** A bug is reproducible but the cause isn't obvious. Stops the model from pattern-matching to a plausible-looking fix that doesn't actually address the cause.

**Why it works:** The default failure mode for AI debugging is generating a fix that "looks like it should work" before the cause is even identified. This prompt makes the model show its work and earn the fix.

---

```
A bug is reproducible. I want a root cause, not a fix.

Before suggesting any code change, do this:

1. State three competing hypotheses for what's actually broken. Rank them by likelihood given only the evidence I've given you. Do not collapse to one until we have evidence that rules the others out.
2. For each hypothesis, name the single cheapest experiment, log line, or query that would falsify it.
3. Tell me what evidence I'd need to see to be 95% sure of the cause. If the evidence I've given you isn't enough, say what's missing.
4. Once we have a cause, only then propose a fix. The fix must include a regression test that fails before the fix and passes after.

Symptoms, repro steps, and what I've tried already:
<paste here>
```

---

This is 1 of 50 prompts in [The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault).
