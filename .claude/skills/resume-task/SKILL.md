---
name: resume-task
description: Pick up the next open item in this project's backlog. Use when the user says "resume", "what's next", "continue the task list", or asks to work on the Thai food recommender app without naming a specific feature.
---

Read `task.md` and `CONTEXT.md` at the project root before doing anything else.

1. In `task.md`, find the first unchecked item. Known open items as of the last survey:
   - Manual browser testing: random-roll behavior, favorites persistence in incognito, modal open/close/focus behavior.
   - Generating the 35 dish images via Codex and dropping them into `image/` — this was blocked on ChatGPT plan usage limits (retry after 2026-09-29, or upgrade). Check current date/availability before assuming it's still blocked.
   - Dark-mode contrast check on a real device.
   - Unscoped backlog: "clear all favorites" button, share-result feature.
   - Reviewing dish list variety.

2. Cross-check the item against `CONTEXT.md` — it's the authoritative domain glossary and also records reversed decisions (e.g. the category filter was rejected then reinstated). Don't reintroduce or re-remove something without checking there first.

3. If the item is manual/browser testing, actually drive it: use the `run` skill or open `index.html` yourself, exercise the interaction, and report what you observed rather than just marking it done.

4. If the item touches domain vocabulary (new UI copy, new concepts), use the `domain-modeling` skill to keep `CONTEXT.md` in sync.

5. After finishing an item, update its checkbox in `task.md` in the same commit/change as the code, and add a one-line note to `CONTEXT.md` if the change affects a domain term or reverses a prior decision.

Remember: this app is deliberately a single `index.html` file with no build step, lint, or test runner — don't introduce tooling to "resume" a task unless the user asks for it.
