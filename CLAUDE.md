# CLAUDE.md

Guidance for any Claude Code agent (or other AI agent) working in this repo.

## What this repo is

Personal portfolio site for Chantamas "Joopjip" Chatraporn, served by GitHub
Pages at https://jjoopjip.github.io/. Static HTML/CSS/JS, no build step, no
package.json, no framework.

- `index.html` — the whole portfolio: a single hash-routed page with four
  views (Home `#/`, Background `#/background`, Application Tracker
  `#/tracker`, Résumé Generator `#/resume-gen`). Routing logic is inline
  `<script>` near the bottom of the file (`routes` map, `render()`).
- `demo/resume-generator.html`, `demo/tracker.html` — standalone interactive
  demo rebuilds of two real local-only apps, embedded via `<iframe>` on the
  corresponding project pages. They replay plausible behavior; they do not
  call any real backend or AI model.
- `assets/` — QR codes pointing at the site (see README.md for regeneration
  notes with `segno`).
- `.nojekyll` — required so GitHub Pages serves files as-is.

Read `README.md` first — it documents the demo philosophy (why the real apps
aren't hosted, what the demos fake vs. replay faithfully) in more depth than
this file does.

## Working in this repo

- No build/install step. Preview with `python3 -m http.server 4000` and open
  `http://localhost:4000`.
- Edits go straight to `main`; GitHub Pages redeploys automatically in about
  a minute. There is no staging environment.
- Keep everything self-contained (inline SVG icon sprite, inline `<style>`
  and `<script>` in `index.html`) — that's a deliberate choice, not an
  oversight. Don't introduce a bundler, framework, or external CDN
  dependency without discussing it first.
- The tracker and résumé-generator demo pages are intentionally fake/sample
  data. Never wire them to a real API, real credentials, or real personal
  data belonging to the site owner.
- This is a portfolio representing a real person's résumé/career content.
  Treat factual claims (employers, dates, degrees) as sensitive — don't
  invent or alter them without the user confirming.

## Session handoff hygiene (required)

This repo uses `SESSION_HANDOFF.md` (and, if it grows large, a companion
`TASKS.md`) to let any agent pick up work cold. **Every agent that makes a
change in this repo must update `SESSION_HANDOFF.md` before ending its
turn** — what you did, what state things are in, and what the logical next
step is. Treat this as part of the task, not an optional courtesy. A task
isn't done until the handoff reflects it.
