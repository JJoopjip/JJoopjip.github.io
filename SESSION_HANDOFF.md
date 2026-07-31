# Session Handoff

Read this first. It's the fast path to understanding what state the repo is
in and what to do next. See `CLAUDE.md` for repo conventions — **every agent
must update this file before ending their turn**, even for small changes.

## Last updated

2026-07-31 — Chantamas Chatraporn (Claude Code session) — the three Bangkok
roles on the Background page were expanded from one paragraph each to a lead
paragraph plus an achievement list. See "Role depth on the Background page".

## Current state

The site is live and working at https://jjoopjip.github.io/. It's a static,
build-free, hash-routed single page (`index.html`) with four views (Home,
Background, Application Tracker, Résumé Generator), plus two standalone demo
iframes under `demo/`. No known bugs or broken links as of this writing.

Recent work (most recent first, from `git log`):

1. Expanded the Winnergy, LG Chem and Otsuka entries on the Background page
   from a single paragraph each into a lead paragraph plus a `.did`
   achievement list, sourced from the résumé master bank.
2. Rebuilt and restored the roles duration timeline on the Background page,
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
2. **Add the SKU scope qualifier to `~/resume_generator/master.yaml`** so
   generated résumés stop understating the portfolio (see above).
3. Nothing else outstanding. The stat row shipped as type-only with provenance
   lines and no meters.

**Don't re-open the dashed part-time bars.** The legend at the top of the chart
names "Part-time" against the dashed swatch, so a reader is told what the
pattern means before they reach a bar. An earlier version of this file raised
"the dashes might read as *estimated*" as an open worry — the legend was already
the answer, and the note was noise. It's gone.

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
- **Sep–Dec 2024 is the first term of the master's**, right after the move to
  Toronto. Four months on the degree and no paid role, which is what starting a
  full-time graduate program in a new country looks like. The study band covers
  the row and the chart is complete there. **This is not a gap and does not need
  flagging, shading, footnoting, or defending** — a previous version of this
  file treated it as a weak spot, which was wrong and got removed.

Keep this in mind before "fixing" an apparent overlap: the overlaps are real.

### Role depth on the Background page (`.did` lists)

The written entries for **Winnergy, LG Chem and Otsuka** each carried one dense
paragraph, which undersold the three full-time roles the owner considers the
core of the résumé. They now render as a short lead paragraph plus a
`<ul class="did">` achievement list — **exactly five bullets each**. `.did` is
styled off the existing `.venues` rule (hairline dash markers, no bullets), one
size up because these are prose sentences rather than venue names.

**Five is a deliberate ceiling, chosen by the owner. Don't exceed it.** An
intermediate version of this work ran to 8/8/7 bullets and the owner's reaction
was that nobody reads that much and people will skip the section entirely. That
judgment was right. Depth alone does not sell a role — depth that survives a
ten-second skim does.

**Every bullet opens with a bolded lead-in phrase** (`.did li b`), so reading
only the bold text still conveys the whole role. This is the mechanism that
makes five substantial bullets skimmable; if you add a bullet, it needs a bold
lead-in too, or it becomes the one line everyone's eye slides past.

The lead paragraph carries **scope** (what the role was, at what kind of
company); the bullets carry **accomplishments**, one idea each.

What got cut when going from 8/8/7 down to 5/5/5, and why it should stay cut:
the lines with no object and no outcome — "coordinated cross-functional
execution", "engaged people across the value chain", "informed marketing
campaigns". Those read as filler and train a reader to skip everything after
them. Winnergy's early-AI-tools line also went: the two AI projects on this same
site demonstrate that far better than a claim does. Nothing was invented to
reach any count.

The content is not new writing. It comes from `~/resume_generator/master.yaml`,
the résumé content bank and the owner's source of truth. Two things about that
file matter here:

- Its `authoring_rules.hard_rules` include **"One page"** — that is a *résumé*
  constraint, not a site constraint. The portfolio has no page limit, which is
  why the one-bullet-per-role compression was never required here. Don't
  re-compress these entries to match a résumé.
- `locked_fields` (metrics, dates, titles, company names) **may be selected and
  reordered but never rewritten**. That rule was respected: every figure on the
  page appears verbatim as it does in the bank.

**Don't draft these entries from the `general` variant alone.** The bank stores
each achievement once with a framing per profile (`bd` / `pm` / `dm` /
`general`). `general` is the *fallback* framing, so it is consistently the most
compressed one — and the compression drops concrete facts that the profile
variants keep. The site is not profile-gated and has no page limit, so the right
source here is the **union of facts across all four variants**, rendered in the
site's voice.

Facts recovered that way, each of which exists in exactly one non-`general`
variant and was invisible on the site before:

- Winnergy — **four modern-trade chains** and a **licensed 10+ SKU feminine-care
  line** (`win_b2c.bd`); **Canva and MailChimp** (`win_engagement.dm`);
  **hospital and clinic** accounts rather than the vaguer "institutional"
  (`win_retention.bd`).
- LG Chem — **competitive fact sheets and product comparisons** feeding
  campaigns and positioning (`lg_intelligence.dm`).
- Otsuka — **domestic manufacturing economics and locally relevant clinical
  data** as the market-access lever (`ot_access.dm`); *"shifting what clinicians
  recommended"*, a real outcome where `general` only says "earning adoption"
  (`ot_clinical.dm`).

Also newly surfaced: the **8-person team** at Winnergy and **early AI-tool
adoption** there (ChatGPT, Canva AI), LG Chem's **positioning /
value-proposition** work and **KPI review cycle**, and Otsuka's
**pharmacovigilance and labeling** work. The 8-person team is the notable one —
people leadership had no representation anywhere on the site before now.

Thai Festival and the York TA entries were left alone. Thai Festival already
uses all four of its bank bullets as prose; the bank explicitly says to keep the
York TA to one bullet ("grading-only scope").

**The bank was fully drained for these three roles, then cut back to the best
five.** Every `bullet` id under `winnergy`, `lgchem` and `otsuka` was drafted
onto the page first, then the weakest were removed. So the page is a *selection*
from the bank, not a shortfall against it — if a role needs different emphasis
for a particular audience, swap a bullet out rather than adding a sixth.

### Two owner decisions from 2026-07-31 — don't re-raise either

- **Confidential figures stay off the site.** The owner will discuss revenue,
  volume, budget and headcount **in an interview, not on a public page**. Do not
  propose adding commercial results to strengthen an entry, and do not treat the
  absence of a revenue figure on the Winnergy B2C launch as a gap to fill. The
  percentages and counts already published are the agreed ceiling.
- **The timeline order is settled and the owner is happy with it.** Boots sits
  above Winnergy because the list is reverse-chronological by end date. Yes,
  `master.yaml`'s renderer rule places part-time roles after full-time ones —
  that rule governs the *résumé*, not this page. Don't reorder the entries.

**The 20+ vs 30+ SKU question is resolved — both numbers are correct.** Confirmed
by the owner on 2026-07-31: **20+ SKUs counts medical devices only; 30+ counts
the electronic-device pipeline as well.** Neither figure was ever wrong; they
have different scopes and the scope was never written down.

The site now states the relationship once, in the Winnergy budget bullet: "four
pipelines — 20+ medical-device SKUs plus a new electronic-device line". The
home-page stat row keeps **30+** (it describes the whole B2C launch, so the
wider scope is the right one there). Don't "fix" either number to match the
other — write the scope instead.

**`~/resume_generator/master.yaml` still says a bare "20+ SKUs"** in
`win_portfolio` and `hl_skus`, with no scope qualifier. That's a separate repo
and was left untouched. It should get the same qualifier, or a résumé generated
from it will keep understating the portfolio.

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
strip (duplicated the bars), red shading over the Sep–Dec 2024 stretch (invented
a problem where there wasn't one — see above), employer names on a second label
line, and a hover tooltip (doesn't work on touch).

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
