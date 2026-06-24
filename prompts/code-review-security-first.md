# Claude Code Security Review Prompt

A staff-level security-first code review prompt for Claude Code, Cursor, and other AI coding assistants — run it before merging anything that touches auth, input handling, or external I/O.

**Use it when:** Before merging anything that touches auth, input handling, or external IO.

**Why it works:** Constraining the lens to security only avoids the model burying real vulnerabilities in style suggestions. The exploit-scenario requirement forces concrete reasoning, not pattern matching.

---

```
Review this code as an application security engineer. Focus only on security issues.

Walk through:
1. Input validation: every external input traced to a sink.
2. Authentication and authorization: every privileged action.
3. Injection vectors: SQL, command, log, template, deserialization.
4. Secret handling: storage, logging, transport.
5. Error and exception leaks: what does the caller learn from a failure?

For each finding: severity (Critical / High / Medium / Low), file:line, exploit scenario in one sentence, fix in one sentence.

Skip generic advice. Skip non-security suggestions. If there are no findings, say so.

Code:
<paste>
```

---

### All 50 prompts — free

This is one of 15 sample prompts from **[The Senior Engineer's AI Prompt Vault](https://sublimecoding.com/vault)** — 50 production-tested prompts for Claude Code and Cursor, plus 5 `.cursorrules` files and 3 `CLAUDE.md` starters (Go, Elixir, AI agents). Free, no login.

→ **[Get the full Vault, free](https://sublimecoding.com/vault)**  ·  **[← all 15 sample prompts](./README.md)**
