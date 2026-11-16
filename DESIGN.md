---
name: Chantamas Chatraporn Portfolio
description: A wayfinding system. Cobalt sign fields, white sign plates, one signal yellow, one heavy grotesque.
colors:
  cobalt: "#1637D6"
  cobalt-deep: "#0F2698"
  cobalt-ink: "#0A1A6E"
  cobalt-tint: "#E7ECFD"
  cobalt-line: "#B9C6F5"
  cobalt-on-field: "#DCE3FF"
  signal-yellow: "#FFC61A"
  ink-navy: "#0C1230"
  slate-mid: "#3B4468"
  slate-faint: "#59628A"
  ground: "#F3F5FA"
  plate-white: "#FFFFFF"
  plate-cool: "#F8F9FD"
  rule: "#D5DBEE"
  rule-soft: "#E4E8F5"
  live-green: "#0B7A4B"
  live-green-tint: "#E5F5EC"
  live-green-line: "#B5DEC6"
typography:
  display:
    fontFamily: "Hanken Grotesk, system-ui, -apple-system, Segoe UI, Roboto, sans-serif"
    fontSize: "clamp(40px, 6.2vw, 72px)"
    fontWeight: 800
    lineHeight: 1.06
    letterSpacing: "-0.035em"
  headline:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: "clamp(30px, 4.2vw, 46px)"
    fontWeight: 800
    lineHeight: 1.06
    letterSpacing: "-0.03em"
  title:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: "24px"
    fontWeight: 800
    lineHeight: 1.06
    letterSpacing: "-0.03em"
  body:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: "17px"
    fontWeight: 400
    lineHeight: 1.6
    fontFeature: "tabular-nums"
  label:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: "15px"
    fontWeight: 700
    lineHeight: 1.3
rounded:
  sm: "10px"
  md: "12px"
  lg: "16px"
  pill: "999px"
spacing:
  xs: "8px"
  sm: "16px"
  md: "28px"
  lg: "48px"
  section: "76px"
components:
  button-email:
    backgroundColor: "{colors.signal-yellow}"
    textColor: "{colors.ink-navy}"
    typography: "{typography.label}"
    rounded: "{rounded.md}"
    padding: "12px 20px"
  button-plate:
    backgroundColor: "{colors.plate-white}"
    textColor: "{colors.ink-navy}"
    typography: "{typography.label}"
    rounded: "{rounded.md}"
    padding: "12px 20px"
  nav-link:
    textColor: "{colors.cobalt-on-field}"
    rounded: "{rounded.pill}"
    padding: "8px 14px"
  nav-link-active:
    backgroundColor: "{colors.plate-white}"
    textColor: "{colors.cobalt}"
  gate-card:
    backgroundColor: "{colors.plate-white}"
    textColor: "{colors.ink-navy}"
    rounded: "{rounded.lg}"
    padding: "26px"
  gate-number:
    backgroundColor: "{colors.cobalt}"
    textColor: "{colors.plate-white}"
    rounded: "{rounded.md}"
    size: "54px"
  stage-switch-current:
    backgroundColor: "{colors.signal-yellow}"
    textColor: "{colors.ink-navy}"
    rounded: "{rounded.md}"
    padding: "16px 20px 18px"
  info-plate:
    backgroundColor: "{colors.plate-white}"
    textColor: "{colors.ink-navy}"
    rounded: "{rounded.lg}"
    padding: "26px 28px"
  tag:
    backgroundColor: "{colors.cobalt-tint}"
    textColor: "{colors.cobalt-ink}"
    rounded: "{rounded.pill}"
    padding: "5px 12px"
---

# Design System: Chantamas Chatraporn Portfolio

## Overview

**Creative North Star: "The Wayfinding System"**

The site behaves like airport and transit signage. Pages are destinations, the three job-search tools are Gate 1, 2 and 3 on one route, and a "You are here" sign says where the visitor stands. Large cobalt fields carry the white sign type, white rounded plates carry facts, and a single signal yellow marks the two places a visitor most needs to find: the email action and the current position.

The register is confident and legible at a glance. One typeface (Hanken Grotesk) is set heavy and tight for signs and regular for reading; numerals are tabular. Structure comes from fields of color, rounded plates, numbered tiles and drawn arrows, not from hairline rules or monospaced labels. Depth is soft and rare.

**Key Characteristics:**
- Cobalt fields at page scale: nav bar, hero, detail headers and closing footer.
- White rounded plates on a cool grey-blue ground (#F3F5FA).
- One heavy typeface; heavy for signs, regular for reading.
- Numbered gate tiles, drawn SVG arrows (CSS-masked), no glyph arrows or icon fonts.
- Yellow is scarce and meaningful.

## Colors

A cobalt-and-white signage palette on a cool ground, with ink-navy text and one yellow.

### Primary
- **Signage Cobalt** (#1637D6): nav bar, hero, detail headers, footer, gate numerals, links and statistic figures. The field color. Cobalt Deep (#0F2698) and Cobalt Ink (#0A1A6E) are the darker steps for text on tints and demo hover states.
- **Field Pale Blue** (#DCE3FF): secondary text, inactive nav links and meta text set on a cobalt field.

### Secondary
- **Signal Yellow** (#FFC61A): the only warm color. Used for the Email action (nav button and first contact chip), the "You are here" current-gate tile, the current-role marker on the experience timeline and in the roles duration chart (with a 1.5px ink outline), the underline under the hero h1 emphasis, and text selection. Focus outlines on cobalt fields also use it.

### Tertiary
- **Live Green** (#0B7A4B, tint #E5F5EC, line #B5DEC6): status only: the "Open to work" dot and the "Try it live" pills.

### Neutral
- **Ink Navy** (#0C1230): text and headings on light surfaces; text on yellow.
- **Slate Mid** (#3B4468): body copy. **Slate Faint** (#59628A): meta, sources, captions.
- **Cool Ground** (#F3F5FA): page background. **Plate White** (#FFFFFF) and **Plate Cool** (#F8F9FD): plates and inset panels. Even-numbered sections alternate to white.
- **Rule** (#D5DBEE) and **Rule Soft** (#E4E8F5): borders and gridlines. **Cobalt Tint** (#E7ECFD) and **Cobalt Line** (#B9C6F5): tag fills, highlighted plates, card borders and the timeline spine.

### Named Rules
**The One Signal Rule.** Yellow marks the email action and "where you are". The build extends "where you are" from the current gate to the current role on timelines. Do not spend yellow on decoration, hover states or generic emphasis.

**The Cobalt Field Rule.** Cobalt fills large areas (bars and headers), not small ornaments. Small cobalt elements are numerals, links and tiles.

## Typography

**Display, body and label font:** Hanken Grotesk (400 to 800), fallback system-ui, -apple-system, Segoe UI, Roboto, sans-serif. No second family.

**Character:** A friendly, sturdy grotesque. At 800 weight with tight tracking it reads like a terminal sign; at 400 to 600 it reads like clear instructions.

### Hierarchy
- **Display** (800, clamp(40px, 6.2vw, 72px), 1.06, -0.035em): hero h1 in white on cobalt, max 17ch. Detail-page h1 uses clamp(36px, 5.6vw, 64px).
- **Headline** (800, clamp(30px, 4.2vw, 46px), 1.06, -0.03em): section h2. Footer h2 clamp(32px, 4.6vw, 52px).
- **Title** (800, 19 to 24px, 1.06 to 1.2, -0.02em): card and gate titles, role titles (22px), stage-switch names (21px).
- **Body** (400, 16 to 18px, 1.6): copy in Slate Mid, measure capped around 56 to 64ch. Base 17px, 16.5px under 860px.
- **Label** (600 to 800, 13 to 16px): tags, pills, meta, nav links (15px 600), buttons (16px 700 to 800). Statistic figures are 800, 26 to 30px, in cobalt.

### Named Rules
**The One Face Rule.** Hanken Grotesk only; hierarchy comes from weight, size and tracking. Numerals stay tabular (set on body).

## Layout

A single 1120px container with 28px side gutters (20px under 420px). Sections pad 76px vertically (56px under 860px); alternate sections swap between ground and white. The hero is a two-column grid (1.55fr and 1fr) with the info plate ordered first in source but placed on the right on desktop, stacking under 860px. The three-gate route is a three-column grid with 36px gaps and a drawn arrow between cards; it becomes one column under 860px. The stage switcher is three columns, one under 720px. Breakpoints: 860px, 720px, 700px, 560px, 420px. At-a-glance proof chips are hidden under 860px, and the nav stacks with the Email button pinned top-right.

## Elevation & Depth

Mostly flat and tonal: depth comes from white plates on cobalt or ground and from 1px or 2px borders. One soft shadow exists.

### Shadow Vocabulary
- **Lift** (`box-shadow: 0 1px 2px rgba(12,18,48,.06), 0 14px 28px -14px rgba(12,18,48,.28)`): the hero info plate, hovered gate cards and the demo window frame.

### Named Rules
**The Plate Rule.** A raised surface is a white plate, optionally with Lift. No hard offset shadows.

## Shapes

Rounded signage plates. Cards and plates use 16px; buttons, tiles and inner panels 12px (stage tiles, gate numerals 12px); small inputs 10px; tags, nav links and pills are fully round (999px). Arrows are drawn SVG masks in currentColor, 3px stroke with round caps. Bullets are 7px circles. The timeline is a 3px spine with 19px ringed nodes.

## Components

### Buttons and chips
- **Email (primary):** Signal Yellow with ink-navy 800 text, 12px radius, 12px 20px padding. In the nav it is a pill.
- **Plate chip (secondary):** white with ink text, same shape; hover lifts 2px (150ms).
- **Nav links:** pills in Field Pale Blue; hover gets a translucent white fill; active is white with cobalt text.

### Gate cards
White, 2px Cobalt Line border, 16px radius, 26px padding. A 54px cobalt numeral tile with a "Gate N · Verb" label leads each card; title, short copy, tags, a green "Try it live" pill and a "View stage" arrow follow. Hover: border to cobalt, lift 3px, Lift shadow. On entry the cards slide in from the left over 650ms with 120ms stagger.

### Stage switcher
Three white tiles on a cobalt header; the current tile is Signal Yellow with an ink "You are here" pill, the others show "Open". Inactive tiles lift 2px on hover.

### Info plate (rail)
White 16px plate with Lift: small uppercase cobalt term labels (12.5px, 700) over 16px descriptions.

### Tags, pills and statistics
Cobalt Tint pills with Cobalt Ink 600 text; "hot" tags invert to cobalt with white text. Statistic rows have a 100px tabular cobalt figure column, a ink label and a faint provenance line.

### Timeline and roles chart
Cobalt ringed nodes on a Cobalt Line spine; the current role node and bar are yellow with an ink outline. Part-time bars are dashed; study bars are tinted with a cobalt end cap.

### Demo apps (demo/)
The embedded demos share the cobalt, ink, ground and rule values and Hanken Grotesk, with flat surfaces (shadows set to none) and 12px or 8px radii. Their CSS keeps legacy token names (sage, apricot, rose) that now hold cobalt and ink values; semantic amber (#9A6700) and red (#D0202F) tints appear for status in the demos only.

### Motion
Page change fades in 250ms. Hover transitions 150 to 200ms; gates enter at 650ms with cubic-bezier(0.16, 1, 0.3, 1). Reveals fade 350ms. Under prefers-reduced-motion all animation, transitions and smooth scrolling are disabled.

### Focus
3px cobalt outline with 3px offset; on cobalt fields the outline is Signal Yellow.

## Do's and Don'ts

### Do:
- **Do** treat every destination as a sign: a numbered tile, a heavy title, a drawn arrow.
- **Do** keep yellow to the email action and "you are here" markers (current gate, current role).
- **Do** place facts on white rounded plates over cobalt or ground, with ink-navy text.
- **Do** draw arrows as SVG masks in currentColor and keep numerals tabular.
- **Do** give any figure a provenance line instead of a decorative chart.
- **Do** honor prefers-reduced-motion by removing animation entirely.

### Don't:
- **Don't** return to a centred hero over a row of identical cards.
- **Don't** introduce cream, terracotta, or Fraunces, Inter or Space Grotesk (confirmed by the owner).
- **Don't** use hairline spec-sheet rules or monospaced labels as the organizing device.
- **Don't** use glyph or emoji arrows and icons; use the inline SVG sprite and masks.
- **Don't** use hard offset shadows; depth is the soft Lift plate or a border.
- **Don't** put a kicker label above a heading.
