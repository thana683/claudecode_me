# AGENTS.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

"วันนี้กินไร" (What to eat today) — a single-page Thai dish randomizer. Click to roll a random dish, favorite it (persisted to `localStorage` under key `thai-food-favorites-v1`), search/filter favorites by name and category, and open a modal for full dish detail (category, description, ingredients).

## Stack and structure

- Pure vanilla HTML/CSS/JS, no framework, no build step, no package manager. Everything lives in `index.html`: inline `<style>` and inline `<script>` (single IIFE). Only external dependency is a Google Fonts `@import`.
- Dish data is a hardcoded `dishes` array inside the script (35 entries: `name, emoji, desc, category, img, ingredients[]`).
- To run: just open `index.html` in a browser (or serve it statically). There is no dev server, no lint, no formatter, no test runner — don't assume any of these exist.
- Keep the app in this single file. A prior fragment file was deliberately merged into `index.html` to avoid two-file sync burden (commit `356fb7d`) — don't re-split it without being asked.

## Domain terms and conventions

- UI copy and domain vocabulary are Thai-first. `CONTEXT.md` is the authoritative glossary (สุ่มเมนู, รายการโปรด, ตัวกรองหมวดหมู่, หน้ารายละเอียดเมนู, etc.) — read it before renaming or reasoning about a domain concept, and use the `domain-modeling` skill when editing it.
- Some past product decisions were reversed and the reasoning is recorded in `CONTEXT.md` (e.g. the category filter was rejected then reinstated) — check there before repeating a decision that's already been made.
- `task.md` is the working backlog/checklist; consult it (and update it) when picking up or finishing work. Testing here is manual/browser-based only — there is no automated test suite.

## Known intentional gap

The `image/` directory is empty on purpose. Each dish's `img` path points into it, but the images haven't been generated yet (blocked on external Codex/ChatGPT usage limits, expected to resume after 2026-09-29). The app already degrades gracefully to the emoji on image load failure — this is tracked, not a bug to silently "fix" by removing the `img` fields.
