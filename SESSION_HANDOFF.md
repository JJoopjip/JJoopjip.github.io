# Session Handoff

Read this first. It's the fast path to understanding what state the repo is
in and what to do next. See `CLAUDE.md` for repo conventions — **every agent
must update this file before ending their turn**, even for small changes.

## Last updated

2026-07-30 — Chantamas Chatraporn (Claude Code session) — roles timeline
restored to the Background page, redesigned. See "The roles timeline" below.

## Current state

The site is live and working at https://jjoopjip.github.io/. It's a static,
build-free, hash-routed single page (`index.html`) with four views (Home,
Background, Application Tracker, Résumé Generator), plus two standalone demo
iframes under `demo/`. No known bugs or broken links as of this writing.

Recent work (most recent first, from `git log`):

1. Rebuilt and restored the roles duration timeline on the Background page,
   and removed the incorrect "Part-time" tag from the York teaching
   assistantship. See "The roles timeline" below for the rules it encodes.
2. Added York University fintech teaching assistantship to the Background
   experience timeline.
3. Added the current Toronto PR internship to the experience timeline.
4. Surfaced project differentiators as highlighted callouts on project
   cards.
5. Reordered/labeled the AI Résumé Generator as "Project 01".
6. Reframed the résumé generator project copy as a "headless Claude agent".
7. Added QR codes (`assets/qr*.svg`/`.png`) pointing at the site, verified
   scannable at print size.
8. Added contact icons/visuals to the Home page.
9. Anonymized the sample data in the tracker demo (no real applications).
10. Linked each project page to its public source repo.
11. Initial site + both interactive demos added.

This session's work (2026-07-29): the **redesign is implemented**. `index.html`
and both demo pages now carry the Spec Sheet identity described below. The
site's structure, routing, copy and demos are otherwise unchanged.

What changed, concretely:

- The Background timeline gained the **Boots pharmacist role** (`baa412f`), and
  the inert `.job.alt` / `.skillcol.s2` attributes were dropped in the same
  commit.
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
`#55534F` fails the protanopia check (OKLab ΔE 4.9 as first measured, 4.5 when
recomputed 2026-07-30 with the Viénot matrix — different simulation, same
verdict, both well under the 6.0 floor). Any chart emphasis must carry a **text
label as well as** the colour.

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

1. **Open it in a browser and review it.** Still the one verification step that
   hasn't happened for the redesign, and it now also covers the restored
   timeline. This machine has no working headless Chromium (`libnspr4.so`
   missing), so the timeline was verified structurally instead: tag balance, CSS
   coverage for every `gt-*`/`k-*` class, no undefined `var()`, all three pages
   served HTTP 200 locally, and every bar's geometry plus every label's pixel
   width recomputed from the font file. **Nobody has looked at it.**
2. Specifically worth eyeballing on the timeline: the **2024–25 boundary**,
   where the thin bars stop and restart across the four study-only months, and
   whether the **dashed part-time bars** read as "part-time" rather than
   "estimated" — that ambiguity is inherent to dashes and was accepted with eyes
   open. The fallback if they read wrong is thin-and-solid.
3. Nothing else outstanding. The stat row shipped as type-only with provenance
   lines and no meters.

**The written record is now continuous** — all 109 months from Jul 2017 to
today, with no gap anywhere. The master's is dated Sep 2024 – Apr 2026
(`04b995c`), which meets the Boots role ending Aug 2024 with no seam.

Recomputed 2026-07-30 from the dates in `index.html`, because an earlier version
of this file claimed "34 months" with two concurrent roles and that figure was
wrong. The real numbers:

- **109 months** covered, Jul 2017 – Jul 2026, **zero** with nothing at all.
- **20 months** carried two *paid* roles at once; **2 months** carried three.
- **36 months** had two or more entries counting the master's as an entry —
  this is where the bogus "34" came from.
- **Sep–Dec 2024 (4 months) has no paid role**, only the master's. This is the
  one thin stretch left, and it's the first term after the move to Toronto.
  It's disclosed, not hidden — don't "fix" it.

Keep this in mind before "fixing" an apparent overlap: the overlaps are real.

### The roles timeline (`.gt-*`) — removed, then rebuilt and restored

**Live on the Background page.** History: shipped `6ad8cbf`, removed `3c04f3f`
(the owner saw it live and it drew attention to the gaps between roles), then
rebuilt and restored on 2026-07-30 after the underlying data changed.

What made it defensible the second time was **missing data being filled in**,
not styling. The part-time Boots pharmacist role (Sep 2021 – Aug 2024) had been
absent from the site entirely; adding it in `baa412f` closed the 2021–22 gap
outright and most of the 2023–24 one, and dating the master's closed the rest.
The case for the chart is **continuity, not chronology**: pharmacy practice
running underneath the commercial roles is the story the bars tell and the prose
can't.

Eight bars on a flat **2017–2027** domain, which is why one year is exactly 10%
and the year gridlines are a `repeating-linear-gradient` rather than ten
elements. If the domain ever changes, every inline `left`/`width` percentage has
to be recomputed — `pct = (year − 2017) × 10`, with end dates expressed as the
first of the following month.

Rules baked into it. **Each of these was an explicit decision by the owner —
don't undo one without asking:**

- **No printed dates and no tooltip.** The bars and the year axis carry the
  period; the written entries below carry it exactly. The owner's reasoning: a
  reader who wants exact dates can drop to the prose, so printing them made the
  same fact appear three times. (This reverses the original build's rule.)
- **Because of that, every bar carries `role="img"` and an `aria-label`** like
  `"Part-time, Sep 2021 to Aug 2024"`. That label is now the *only* text a
  screen reader can get from a bar, and it also announces full/part-time, which
  is otherwise encoded as a dash pattern and therefore visual-only. If you edit
  a bar, edit its label.
- **Part-time roles are thinner (5px) and dashed**, with solid 1px end caps so
  the dashes don't clip mid-stroke at the date boundaries. Part-time is Boots
  and Hospitality only.
- **No employer names anywhere in the chart**, by request. The prose has them.
- **Every label is a job title, not a department, and nothing is abbreviated.**
  PR/BD/NPD were all spelled out. The label column is **190px**, sized against
  the real font file: the longest is "Business Development Executive" at
  177.5px. Re-measure before lengthening any label.
  - Two titles are shortened to fit, deliberately: "Business Development
    Manager" (from "…& Online Marketing Manager") and "Senior Project
    Specialist" (from "…, New Product Development"). **Keep the title half, not
    the department half** — the Otsuka row is the only evidence on the chart
    that project management predates the master's, and it's meant to rhyme with
    "M.S. Project Management" four rows up.
- The two live roles carry the accent **and** a text label, because signal red
  and context graphite are near-identical under protanopia (OKLab ΔE 4.5
  against a 6.0 floor). Never let emphasis rest on the red alone.
- Graduate study is a **solid** light band with a hard right edge at graduation.
  It used to fade at the left because only the year was known; now that it's
  dated Sep 2024 the fade is gone. Don't reintroduce it.
- The `Current` / `This term` tags sit to the **left** of their bars. Those bars
  end at the right edge of the domain, so a trailing label overflows the lane
  and forces a horizontal scroll. Don't move them back.

Rejected along the way, so don't propose them again: a month-by-month coverage
strip (duplicated the bars), red shading over the Sep–Dec 2024 stretch (drew the
eye to the one weak spot), employer names on a second label line, and a hover
tooltip (doesn't work on touch).

Also corrected in this line of work, both confirmed by the owner: front-of-house
runs from **Jan 2025** (not Apr 2025), the master's is dated to graduation in
**Apr 2026**, and the York teaching assistantship is **not part-time** — it's a
full-time contract, so the `tag-extra` reading "Part-time · Teaching
assistantship" was removed outright rather than reworded. The role title already
says what it is.

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
