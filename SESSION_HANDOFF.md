# Session Handoff

Read this first. It's the fast path to understanding what state the repo is
in and what to do next. See `CLAUDE.md` for repo conventions — **every agent
must update this file before ending their turn**, even for small changes.

## Last updated

2026-07-29 — Chantamas Chatraporn (Claude Code session)

## Current state

The site is live and working at https://jjoopjip.github.io/. It's a static,
build-free, hash-routed single page (`index.html`) with four views (Home,
Background, Application Tracker, Résumé Generator), plus two standalone demo
iframes under `demo/`. No known bugs or broken links as of this writing.

Recent work (most recent first, from `git log`):

1. Added York University fintech teaching assistantship to the Background
   experience timeline.
2. Added the current Toronto PR internship to the experience timeline.
3. Surfaced project differentiators as highlighted callouts on project
   cards.
4. Reordered/labeled the AI Résumé Generator as "Project 01".
5. Reframed the résumé generator project copy as a "headless Claude agent".
6. Added QR codes (`assets/qr*.svg`/`.png`) pointing at the site, verified
   scannable at print size.
7. Added contact icons/visuals to the Home page.
8. Anonymized the sample data in the tracker demo (no real applications).
9. Linked each project page to its public source repo.
10. Initial site + both interactive demos added.

This session's work (2026-07-29): the **redesign is implemented**. `index.html`
and both demo pages now carry the Spec Sheet identity described below. The
site's structure, routing, copy and demos are otherwise unchanged.

What changed, concretely:

- `index.html` — the entire `<style>` block was rewritten in the Spec Sheet
  idiom. **All existing class names were kept**, so the markup continues to
  work; what changed is the tokens, the radii (22px → 2px), the shadows
  (removed — 1px rules carry structure now), and where the accent is allowed to
  appear (12 references total, roughly one per screen).
- Hero gained a **metadata rail** (`.hero-grid` + `.rail`) listing location,
  focus, sectors and credentials.
- The stat row (`.impact`) is now one bordered row with hairline cell dividers,
  a mono category label (`.stat .u`) and a **provenance line** (`.stat .src`)
  under each figure. The growth figure now reads `×2` rather than `100%`, which
  is the same fact stated the way readers actually parse it.
- Fonts: Fraunces / Hanken Grotesk / JetBrains Mono → **Schibsted Grotesk +
  Martian Mono**. Favicon is now a red square; `theme-color` added.
- The Background page gained a **roles duration timeline** above the written
  entries (see its own section below).
- `demo/*.html` — both already had a `:root` token block, so they were
  retargeted in place. Inter/Nunito → Schibsted Grotesk / Martian Mono. Their
  semantic colours were remapped, not flattened: sage → status green
  `#147A4B`, apricot → attention ochre `#9A6700`, rose → accent red `#D0202F`.

Two typographic fixes worth knowing about, both from measuring the actual font:
Martian Mono has a 0.700em advance on every glyph, so `.stat .src` needed
tighter tracking to keep the longest provenance line on one row, and `.langs`
was moved off mono (a full sentence in a label face reads as a code dump).

**Not verified in a browser.** This machine has no working headless Chromium
(`libnspr4.so` is missing and installing system packages was out of scope), so
verification was structural: class/CSS coverage, no undefined `var()`
references, tag balance, live fetch of all three pages, font-URL resolution,
and glyph-advance arithmetic for the tightest cells. **Someone should still
open it and look.**

Inert leftovers: `.job.alt` and `.skillcol.s2` remain in the markup but have no
rules any more — the new palette has no colour alternation, since green is
reserved for status. Harmless; kept in case a future variant wants them.

To recover the previous design, `git diff` / `git checkout 8f62e60 -- index.html
demo/` — the old version is in git history, not in any scratch file.

Previous session (2026-07-24): created `CLAUDE.md` and this handoff file. No
content or code changes to the site itself.

## Redesign in progress — read before touching styles

The site currently uses cream `#FBF6EF` + terracotta `#E4A182` + sage
`#89A184` with a Fraunces display face. That is effectively Anthropic's brand
palette, so the site reads as "made with Claude" to anyone who uses Claude.
The owner wants that gone.

### Decided (do not re-litigate)

**Structure — "Spec Sheet".** The page as a technical datasheet: metadata rail
on the left, hairline 1px rules instead of shadows, ~2px corner radius instead
of 22px, mono figures, and the accent colour used **once per screen** rather
than on eyebrows/links/tags/dots at the same time.

**Palette — Graphite & Signal Red.**

```
--paper:#F1F1EF   --surface:#FFFFFF  --ink:#101010    --mid:#55534F
--faint:#8A8781   --rule:#DCDBD6     --accent:#D0202F --tint:#FCEEEF
--accent-line:#F0C3C7              --ok:#147A4B     --ok-tint:#EDF7F1
```

**Type — Schibsted Grotesk** (headings + body) with **Martian Mono** (labels,
IDs, all figures). Both are on Google Fonts:

```
family=Schibsted+Grotesk:wght@400;600;700&family=Martian+Mono:wght@400;600
```

Avoid Fraunces (the current display face), Inter, and Space Grotesk — all three
read as AI-designed.

**Numbers.** The five home-page figures stay typographic — no sparklines. Only
`90%` (of customers) and `3.9` (of 4.0) have a real denominator, so only those
two may ever carry a meter. Recommended addition is a **provenance line** under
each figure; three of the five come from Winnergy Medical, 2022–23.

**Charting constraint.** Signal red `#D0202F` against context graphite
`#55534F` fails the protanopia check (OKLab ΔE 4.9, floor 6.0). Any chart
emphasis must carry a **text label as well as** the colour.

The design directions, palette options, type specimens and stat-row treatments
were delivered as private published pages on the owner's account. **Those links
are deliberately not recorded in this public repo** — ask the owner for them, or
work from the tokens and rules above, which is everything the pages concluded.

**Shipped live.** Committed as `1b6168a` and pushed to `main` on 2026-07-29;
GitHub Pages redeployed in about 30 seconds and
https://jjoopjip.github.io/ now serves the new identity (verified: new font
link present, zero references to the old palette, both demo pages HTTP 200 on
the new fonts). To roll back: `git revert 1b6168a && git push`.

## What comes next

1. **Open it in a browser and review it** — it is live and was never viewed in
   a browser before shipping (no working headless Chromium on the dev machine;
   see above). This is the one verification step that hasn't happened.
2. Nothing else is outstanding. The stat row shipped as type-only with
   provenance lines and no meters; the roles timeline shipped in `6ad8cbf`.

### The roles timeline (`.gt-*`, Background page)

Shipped. Seven bars on a flat **2017–2027** domain, which is why one year is
exactly 10% and the year gridlines are a `repeating-linear-gradient` rather than
ten elements. If the domain ever changes, every inline `left`/`width` percentage
has to be recomputed — `pct = (year − 2017) × 10`, with end dates expressed as
the first of the following month.

Rules baked into it, worth keeping if you touch it:

- Every range is **printed as text beside its own bar**, so the chart is never
  the only place a date lives. That's why there is deliberately no tooltip.
- The two live roles carry the accent **and** a text label, because signal red
  and context graphite are near-identical under protanopia (see above).
- Graduate study has a hard right edge at graduation (Apr 2026) and a **faded
  left edge** — the starting year is known, the month is not, and fading is
  more honest than picking one. If the owner supplies the start month, replace
  the gradient with a solid fill and set `left` accordingly.
- The `Current` / `This term` tags sit to the **left** of their bars. Those bars
  end at the right edge of the domain, so a trailing label overflows the lane
  and forces a horizontal scroll. Don't move them back.

Dates corrected in the same commit, both confirmed by the owner: front-of-house
now runs from **Jan 2025** (not Apr 2025 — its own venue list already said Jan,
so the parent entry had been inconsistent), and the master's is dated to
graduation in **Apr 2026**.

Answered earlier and already applied — don't re-ask: the stat row gets
provenance lines and no sparklines; only `90%` and `3.9` would ever be allowed a
meter, and Option A ships without them.

Longer-term, unchanged from before (not commitments): keep extending the
Background timeline as the owner's career progresses; add projects if more
tools get built; keep QR codes and README in sync with any URL/branding
change.

## How to verify things still work

```bash
python3 -m http.server 4000
# open http://localhost:4000, click through all four routes,
# and open both project pages to confirm the demo iframes load.
```

There's no automated test suite or CI — verification is manual, in a
browser.

## Handoff checklist for the next agent

- [ ] Update "Current state" and "Last updated" above.
- [ ] Prepend your work to "Recent work" (or fold into the git-log-derived
      list if it's stale — `git log --oneline -15` is the source of truth
      for history; this file is a curated summary, not a replacement).
- [ ] Update or clear "What comes next" based on what you did and what you
      learned.
- [ ] If a task list grows large enough to warrant its own file, create
      `TASKS.md` and link it here instead of inlining it.
