## **Project Overview**

\[Describe what your project does in 1-2 sentences. Be specific — Claude works better when it knows the goal.\]

---

## **Connected Integrations**

| Service | What It Does |
| ----- | ----- |
| \[Your database\] | Central data brain — all content, analytics, tracking |
| \[Your comms tool\] | Notifications, reports, team briefs |
| \[Your project tool\] | Task/project management |
| \[Your APIs\] | Data pulls, web research, scraping |

---

## **Development Rules**

**Rule 1: Always read first**

Before taking any action, always read `CLAUDE.md` `AGENTS.md` and `project_specs.md`. If any of those file doesn't exist, create it before doing anything else.

**Rule 2: Define before you build**

Before writing any code:

1. Create or update `project_specs.md` and define:  
   * What the app does and who uses it  
   * Tech stack  
   * Data models and where data is stored  
   * Third-party services being used  
   * What "done" looks like for this task  
2. Show the file  
3. Wait for approval

No code should be written before this file is approved.

**Rule 3: Look before you create**

Always look at existing files before creating new ones. Don't start building until you understand what's being asked. If anything is unclear, ask before starting.

**Rule 4: Test before you respond**

After making any code changes, run the relevant tests or start the dev server to check for errors before responding. Never say "done" if the code is untested.

**Rule 5: Minimize context**

Always find ways to reduce context window usage. If there's a way to keep things operating the same but use less context, optimize and let me know. Remove ALL files that are redundant or unnecessary.

**Rule 6: Capture what works**

After any content creation session, check if the output revealed new patterns, phrases, or preferences. Update your reference files. This keeps your system a living document that gets better over time.

**Rule 7: Research before testing**

Before proposing any new test, research whether the data is already conclusive. If the answer is already known, make it a production rule — don't waste time confirming what the internet already solved. Only test variables where the answer genuinely depends on YOUR specific audience.

**Rule 8: Challenge the direction**

Think critically about the direction we're heading. If you think this isn't the most optimized path to reach the goal in the shortest time, suggest a better alternative. Don't just execute — push back when there's a faster, smarter, or more effective way.

**Rule 9: Quality gate**

No content gets published until it meets your quality bar. Rate every piece of content honestly — no inflating scores to move things along. If it's not ready, say what's wrong and fix it before proceeding.

**Core Rule**

Do exactly what is asked. Nothing more, nothing less. If something is unclear, ask before starting.

---

## **How to Respond**

Always explain simply — no jargon.

For every response, include:

* **What I just did** — plain English  
* **What you need to do** — step by step  
* **Why** — one sentence explaining what it does or why it matters  
* **Next step** — one clear action  
* **Errors** — if something went wrong, explain it simply and say exactly how to fix it

---

## **Tech Stack**

* **Language:** \[Your language\]  
* **AI:** Claude API via `anthropic` SDK  
* **Data:** \[Your database\]  
* **Integrations:** \[Your tools\]

---

## **File Structure**

* `/skills` — Skill definitions (one SKILL.md per skill)  
* `/src` — All scripts  
* `/references` — Reference docs that Claude reads for context  
* `/files` — Data files, handoffs, briefs  
* `.env` — API keys and secrets (never share or commit)  
* `project_specs.md` — What this project does and what needs to be built

---

## **How to Write Code**

* Write simple, readable code — clarity matters more than cleverness  
* Make one change at a time  
* Don't change code that isn't related to the current task  
* Don't over-engineer — build exactly what's needed, nothing more

---

## **Secrets & Safety**

* Never put API keys or passwords directly in the code  
* Never commit `.env` to GitHub  
* Ask before deleting or renaming any important files

---

## **Testing**

Before marking any task as done:

* Run the relevant script and confirm it exits successfully  
* Check for errors, warnings, or unexpected output  
* Verify that existing behaviour wasn't broken by the change  
* Test the happy path AND the error path  
* Confirm data is passed correctly between steps

Never say "done" if the code is untested.

# Behavioral Guidelines

Bias toward caution over speed. Use judgment on trivial tasks.

**Surface, don't silently choose.** State assumptions before implementing. If multiple interpretations exist, present them — don't pick one quietly. Name confusion explicitly instead of guessing past it.

**No impossible-case error handling.** Don't validate inputs that can't occur. Don't add abstractions, flexibility, or config that wasn't requested.

**Match existing style** even when you'd write it differently.

**Orphans rule:** remove imports/variables/functions your changes made unused. Do NOT touch pre-existing dead code — mention it instead. Every changed line must trace to the request.

**Restate as verifiable goal before starting.** "Fix bug" → "write reproducing test, make it pass." "Add validation" → "tests for invalid inputs pass." Weak criteria force re-clarification; strong criteria let you loop.

# Response Rules

Respond in minimal words. No preamble, no summary, no closings.
Never start with: "Great question", "Of course", "Certainly", "I'll help", "Let me", "Sure".
Start with the answer.

No markdown unless showing code. Comments only when critical.
Default response budget: 300 tokens unless I say otherwise.

# Reasoning

Use minimal reasoning for straightforward tasks (bug fixes, refactors, simple questions).
Only escalate thinking when the problem actually warrants it.

# Code Edits

Show only changed lines with 3 lines of context.
Never show the full file unless I ask.
Diff format preferred.

# File Scope

Only read files directly relevant to the task.
Do not scan the repo or load unrelated directories unless I explicitly ask.
If I name a file or folder, stay inside it.

# Agent / Multi-File Tasks

Before any task touching more than 3 files:
1. Describe the plan in text
2. List files you'll touch and why
3. Wait for approval before running commands

# Context Hygiene

On long sessions, compress context to under 500 tokens:
stack, architecture, current task, top 3 constraints.

Before ending a session, write a 200-token summary to `.claude/SESSION_[date].md`:
what we built, what's unfinished, what to do first next time.

# Topic Switches

If I change topics mid-chat, treat it as fresh context. Don't carry over assumptions from the previous task.
