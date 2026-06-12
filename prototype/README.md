# Prototype

A fast, throwaway **visual prototype** of the homepage — used to *see and iterate*
on the design before building the real Next.js app. It implements
`docs/DESIGN_DIRECTION.md` (palette, type, sections, "nature meets hippie Star
Trek" art direction) as a single self-contained HTML file.

This is **not** the production code. It exists so we can change the look quickly
and cheaply (no Figma quota, no build), agree on it, then rebuild it properly in
the real stack (Next.js + Tailwind + the persistent R3F canvas for real 3D).

## Files

- `homepage.html` — the prototype (inline CSS, Google Fonts, CSS-gradient
  "luminous-organic" glow standing in for the hero 3D). Open it in any browser.
- `homepage-*.png` — generated screenshots (desktop / hero / mobile). **Not
  committed** (gitignored) — regenerate with the command below.

## Preview / re-render

Open `homepage.html` directly in a browser, or regenerate screenshots:

```bash
cd /tmp && mkdir -p shot && cd shot && npm i puppeteer@23
node /home/user/templet-/prototype/shot.js   # (script that screenshots the file)
```

## Status

Homepage **v1**. Uses placeholders for the open decisions in
`docs/DESIGN_DIRECTION.md` (jurisdiction, credentials, free-vs-paid discovery
call, e-commerce tool). Iterate here, then port to the real app.
