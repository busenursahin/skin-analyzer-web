# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

The static website for **FaceGlow – AI Skin Scanner** (iOS app). It is plain HTML, CSS and JS with no build step and no framework. The App Store listing links to the privacy and terms pages, so their URLs must not change.

Pages:
- `index.html`: the landing page. A hero with a live HTML result card, real app screenshots (`img/screens-*.webp`), features, a privacy diagram, FAQ and footer.
- `skin-quiz.html`: a 10-question skin-type quiz. It scores in the browser. `localStorage` is wrapped in try/catch, and the page never uses `alert()`.
- `privacy-policy.html`, `terms-of-use.html`: legal pages with a table of contents. Their shared styles are in `inner.css`.

Related projects: `../SkinAnalyzerAI` (iOS app), `../skin-analyzer-api` (backend), `../busilog` (macOS admin app).

## Running

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Design System

The site was built with the `design-taste-frontend` skill (kind: software).
- `assets/system.css` and `assets/system.js` are that kit's tokens, grid, buttons, motion and hover layer. Use the kit's classes and tokens, and keep page-specific CSS small.
- `assets/` holds copies of the kit (layout, motion, diagrams, icons, …). Do not edit them by hand.
- `.taste-skill/` (gitignored) holds the skill's history and its `waivers.json` (two accepted gate exceptions). `shots/` (gitignored) holds check screenshots.
- To redesign or change a layout, run the skill again and pass its gate (`gate.mjs`, `consistency.mjs`).

## Privacy Policy Must Match the Code

`privacy-policy.html` is the public promise. Keep it consistent with `../skin-analyzer-api` and the iOS app:
- What is collected: photos, analysis results, the anonymous RevenueCat subscription ID, subscription status, and app and device info.
- Data is never linked to a person, and photos are not used for AI training (the AI provider is called with `store: false`). The site says "AI system" and never names the provider (OpenAI); keep it that way.
- Not stored: name, email, phone, IP address, country or any location.

If the API starts collecting something new, update the policy in the same change.

## Leftovers

`styles.css`, `logo.jpg` and `ss/` belong to the old design and are no longer referenced. They can be deleted.
