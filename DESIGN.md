---
name: Chantamas Chatraporn Portfolio
description: A sticker world in three themes (Light, Dark, Cute). One layout, restyled by tokens. Pink bear mark, pastel panels, the owner's own characters.
colors:
  light-page: "#FFFFFF"
  light-ink: "#1D1B22"
  light-panel: "#FDF0F6"
  light-accent: "#C2307A"
  dark-page: "#17131C"
  dark-ink: "#F5EFF7"
  dark-panel: "#241B2D"
  dark-accent: "#FF8FBF"
  cute-page: "#FFF9FB"
  cute-ink: "#2B2330"
  cute-pink: "#FFC8DD"
  cute-mint: "#BDEBD7"
  cute-blue: "#C8DFFF"
  mark-pink: "#E64A8D"
typography:
  body: "Figtree (Light, Dark) or Nunito (Cute)"
  display: "Figtree 800 (Light, Dark) or Baloo 2 800 (Cute)"
---

# Design System: Chantamas Chatraporn Portfolio

## Overview

**Creative North Star: "The Sticker Sheet"**

One layout, three themes, chosen by the visitor with the Light / Dark / Cute switcher in the nav. The choice is stored in `localStorage` under `cc-theme`; Light is the default. Themes are token sets on `html[data-theme]` in `index.html`, so every page and the three demos follow the same switch (the demos listen for a `postMessage` from the parent page and read the same key when opened alone).

- **Light (planner page):** white dot-grid page, near-black outlines (2px), index-divider tabs in pink, blue, mint and yellow for the nav, washi-tape strips on cards, a pink highlighter mark on the hero headline, raspberry accent `#C2307A`, Gabarito 800 headings over Figtree. Calm and professional. These rules sit under `html:not([data-theme="dark"]):not([data-theme="cute"])` in `index.html`.
- **Dark:** deep plum page, light pink accent `#FF8FBF`. The same layout for night reading.
- **Cute:** the owner's chosen "B" look. Pastel pink, mint and blue panels, 3px ink outlines, hard 6px offset shadows, 28px radii, Baloo 2 headings and Nunito body.

## Mark and favicon

One mark serves as logo and favicon: a solid pink bear head whose two eyes are white C letters ("CC", initials of Chantamas Chatraporn). The Cs act as the bear's eyes (radius 7.5, stroke 6.5, centres 34 and 66, 50-degree openings, so never "OC" or an infinity sign), with a nose and a small mouth below them. Files: `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`. In the nav it is inline SVG recoloured by theme (`--mark`, `--mark-ink`).

## Characters

Mianmian (pink bearcat) and Rourou (raccoon) are the owner's original characters. Eight still stickers in `assets/stickers/` (Mianmian: awestruck, guilty, overwhelmed, thinking; Rourou: celebrating, in love, sad hug, sleeping) appear as small decoration (one Mianmian on the home Stickers card, a small pair in the footer) and as the full set on the Stickers page. The hero carries no characters: the site is for job hunting. They are stills; motion is CSS only (a slow float in the hero and footer, a wiggle on hover) and is switched off for reduced motion. The existing animated Mianmian files are not used because they have cropped frames and colour patches.

## Rules

- **Do** keep the accent for the primary action (Email) and small markers; panels carry the pastel colour.
- **Do** let the stage cards, feature cards and sticker cards cycle pink, blue and mint in Cute; in Light and Dark use plain surfaces.
- **Do** keep outlines in Cute at 3px ink with the hard shadow, and 1.5px soft lines in Light and Dark.
- **Do** keep every text and background pair at WCAG AA in all three themes.
- **Don't** use small labels above headings, icon-card grids, colored side borders, or em and en dashes in prose.
- **Don't** use cream with terracotta, Fraunces, Inter or Space Grotesk (the look must not read as Claude's).
- **Don't** add more themes or animated sticker files without asking the owner.

## Components

Nav (mark, links, Email, theme switcher), a Download résumé (PDF) chip beside Email, LinkedIn and GitHub (`assets/Chantamas_Chatraporn_Resume.pdf`, phone number redacted), hero card with sticker pair, destination cards, stat rows with provenance lines, stage cards (three, each linking to a stage page) with a stage switcher, timeline, demo window frame, sticker gallery, closing card with characters. Component CSS lives in the single `<style>` block of `index.html`.
