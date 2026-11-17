# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Plain static HTML, CSS and JavaScript. No build step, no framework. Everything is inline in `index.html` (styles, scripts, SVG icon sprite) except three standalone demo pages in `demo/`. The only external request is the Google Fonts stylesheet (Figtree, Nunito, Baloo 2). The site has three visitor-selectable themes (Light default, Dark, Cute). The server pulls `main` and serves files as they are.

## Users

Recruiters and hiring managers for project management, business development and strategy roles in Toronto. They skim for a few minutes, often on a phone, and decide whether to reply. Secondary: contacts who open the link from a résumé, a business card or a QR code.

## Product Purpose

A personal portfolio for Chantamas "Joopjip" Chatraporn: PMP-certified project manager and commercial professional with seven years in pharma, medtech and consumer health, based in Toronto. Success is a recruiter emailing her. Email is the main action; LinkedIn is secondary.

## Positioning

She is a project manager who also builds her own tools. The Job Search System (a job board, an AI résumé generator and an application tracker) and the animated sticker packs are working proof, shown as interactive demos built on invented data.

## Operating Context

The site is a single hash-routed page: Home, Background, Job Search System (three stages: Job Board, Résumé Generator, Application Tracker) and Stickers. Demos run in the browser and call no backend or AI model. The same facts are mirrored in `about.md` and `llms.txt` for machine readers.

## Capabilities and Constraints

- Static files only; keep everything self-contained.
- Factual claims (employers, dates, degrees, credentials) are sensitive: never invent or change them without the owner confirming.
- No confidential figures on the public site (revenue, volumes, budgets, headcount). Maximum five bullets per role.
- Demos use invented companies and postings only. Nothing real from the owner's job search appears.
- The server does not serve dotfiles, CLAUDE.md, SESSION_HANDOFF.md or README.md.

## Brand Commitments

- Name: Chantamas Chatraporn, nickname Joopjip.
- The look must not read as AI-generated: no cream and terracotta grounds, and none of the faces Fraunces, Inter or Space Grotesk. The owner rejected the Wayfinding signage look (cobalt, yellow, Hanken Grotesk) and chose a pink "sticker" world: a pink bear "CC" mark used as logo and favicon, the owner's own characters, and three themes (Light, Dark, Cute).
- Copy should sound like a person wrote it.

## Evidence on Hand

Real career history on the Background page, three interactive demos (`demo/job-search.html`, `demo/resume-generator.html`, `demo/tracker.html`), sticker packs live on WhatsApp and WeChat (LINE in review). No testimonials, no press, and no PDF résumé on the site; do not fabricate any.

## Product Principles

1. Contact is one step away from every page.
2. Show the work running, not a description of it.
3. Every claim is one the owner has confirmed.
4. Readable on a phone in under a minute.

## Accessibility & Inclusion

Meet WCAG AA contrast, keep keyboard focus visible, and respect reduced motion.
