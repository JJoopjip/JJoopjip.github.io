# jjoopjip.github.io

Personal portfolio for **Chantamas “Joopjip” Chatraporn** — project manager and
commercial professional in pharma, medtech and consumer health, Toronto.

**Live:** https://jjoopjip.github.io/

## What's here

| Path | Purpose |
|---|---|
| `index.html` | The portfolio — a hash-routed single page (Home / Background / Tracker / Résumé Generator). |
| `demo/resume-generator.html` | Interactive demo of the AI Résumé Generator. |
| `demo/tracker.html` | Interactive demo of the Job Application Tracker. |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is (no Jekyll build). |

The two project pages embed their demo via an `<iframe>` inside the browser-chrome
frame, so a visitor can use the interfaces without installing anything.

## About the demos

Both real apps run **locally only** — the résumé generator calls an AI model and
reads a private career-history file (`master.yaml`), and the tracker holds real
applications. Neither can be hosted publicly without exposing that data.

So the demos are faithful **rebuilds of the interfaces**, running entirely in the
browser:

- They use the real apps' palette, layout and copy.
- The résumé generator demo replays the **actual step lines** the real pipeline
  prints (`web/app.py`), with plausible pacing. It does not call an AI model.
- Every application in the tracker demo is **invented sample data**.
- Each demo carries a visible **Demo** banner. Nothing typed into them is sent
  anywhere.

Source for the real generator: https://github.com/JJoopjip/ai-resume-generator

## Editing

No build step — plain HTML/CSS/JS. Edit, commit, push to `main`; GitHub Pages
redeploys in about a minute.

```bash
# preview locally
python3 -m http.server 4000
# then open http://localhost:4000
```

## QR codes

`assets/` holds QR codes pointing at https://jjoopjip.github.io/

| File | Use | Notes |
|---|---|---|
| `qr.svg` / `qr.png` | print — résumé, business card | Black on white, 29×29, error level Q (25%). Verified to scan down to ~10mm printed. |
| `qr-brand.svg` / `qr-brand.png` | slides, web | Portfolio palette + peach dot, 33×33, error level H (30%) to absorb the dot. Needs ~15mm; use the plain one when small. |

SVG is preferred wherever it's supported — it stays crisp at any size.
Regenerate with `segno`; every file above was decode-verified back to the URL.
