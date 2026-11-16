# CLAUDE.md

Guidance for any Claude Code agent (or other AI agent) working in this repo.

## What this repo is

Personal portfolio site for Chantamas "Joopjip" Chatraporn, served at
https://chantamas.com/ (a server run by a friend, behind Cloudflare; see
"Deploying" below). Static HTML/CSS/JS, no build step, no
package.json, no framework.

- `index.html` — the whole portfolio: a single hash-routed page with six
  routes (Home `#/`, Background `#/background`, Job Search System stages
  `#/job-search`, `#/resume-gen`, `#/tracker`, and Stickers `#/stickers`). Routing logic is inline
  `<script>` near the bottom of the file (`routes` map, `render()`).
- `demo/job-search.html`, `demo/resume-generator.html`, `demo/tracker.html` —
  standalone interactive demo rebuilds of three real local-only apps (invented
  data only), embedded via `<iframe>` on the
  corresponding project pages. They replay plausible behavior; they do not
  call any real backend or AI model.
- `assets/` — QR codes pointing at the site (see README.md for regeneration
  notes with `segno`).
- `.nojekyll` — leftover from GitHub Pages hosting; harmless, leave it.

Read `README.md` first — it documents the demo philosophy (why the real apps
aren't hosted, what the demos fake vs. replay faithfully) in more depth than
this file does.

## Working in this repo

- No build/install step. Preview with `python3 -m http.server 4000` and open
  `http://localhost:4000`.
- Edits go to `main`, but **pushing does not publish**: the live site only
  changes when you run the deploy step (see "Deploying"). There is no staging
  environment.
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

## Deploying (chantamas.com)

The site is served by a server run by a friend (Yang), behind Cloudflare. The
server pulls this repo's `main` and serves the files exactly as they are, as
static files. Nothing is built. A deploy = the server pulls `main` from GitHub,
then restarts the site's container.

**Always ask the user whether to deploy, every time a change is ready** (after
committing and pushing, or when you'd otherwise report the work as done). Don't
deploy without a yes, and don't skip the question because the change is small.

To deploy, once the user says yes:
1. Commit and push to `main` on GitHub. The server deploys only what is on
   GitHub, never local changes.
2. Run `ssh chantamas-deploy` **once**. It runs the deploy on the server and
   prints git's output ("Already up to date." or the changed files) and the
   container restart. The key can do nothing else: any other command is
   ignored and there is no shell.
3. Verify on https://chantamas.com/ (HTML updates right away; Cloudflare may
   cache images, CSS and JS for a while: reload with cache bypassed, or ask the
   owner to purge it: Cloudflare dashboard → Caching → Configuration → Purge
   Everything).

Rules:
- **Never put the server's IP address, SSH port, user name or SSH config in
  this repo**, in commits or in any file here. The repo is public. The
  connection details live only in the owner's `~/.ssh/config` under the name
  `chantamas-deploy`.
- **Don't add deploy, Docker, nginx or server files to this repo** (e.g.
  `aideploy.env`, `deploy/`). The server side is managed by Yang.
- **Never force-push to `main` or rewrite its history** (no rebase or amend of
  pushed commits). The server only fast-forwards, so a rewritten `main` stops
  all deploys until Yang fixes it by hand.
- Everything on `main` is public at chantamas.com, except dotfiles (`.git`,
  `.nojekyll`), `CLAUDE.md`, `SESSION_HANDOFF.md` and `README.md`, which the
  server doesn't serve. Don't put anything private in other files.
- File paths are case-sensitive on the server (`about.md` ≠ `About.md`).

If something goes wrong:
- `Permission denied (publickey)`: the SSH config is missing or points at the
  wrong key; it must use `~/.ssh/deploy` under `Host chantamas-deploy`.
- `Host key verification failed`: first connection; the owner must verify the
  fingerprint with Yang and accept it interactively (`! ssh chantamas-deploy`).
  Never disable host-key checking.
- "Not possible to fast-forward" / "diverging branches": `main` was rewritten.
  Don't force-push to fix it; tell the owner to contact Yang.
- "Connection refused" or timeouts after several quick attempts: the server
  rate-limits SSH. Wait about 10 minutes, then try once.
- A Cloudflare 5xx error page, or anything needing the server changed
  (headers, redirects, subdomains): the owner contacts Yang; you can't change it.

## Session handoff hygiene (required)

This repo uses `SESSION_HANDOFF.md` (and, if it grows large, a companion
`TASKS.md`) to let any agent pick up work cold. **Every agent that makes a
change in this repo must update `SESSION_HANDOFF.md` before ending its
turn** — what you did, what state things are in, and what the logical next
step is. Treat this as part of the task, not an optional courtesy. A task
isn't done until the handoff reflects it.
