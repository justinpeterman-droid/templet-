# Hometown Serenity — Hypnotherapy Practice Website

A conversion-focused, **therapeutic hypnotherapy practice website**: marketing +
education + digital-audio store, organized around one dominant call-to-action
("Book a Free Discovery Call") with a free downloadable audio as the
email-capture lead magnet. Built to be calm, fast, accessible, and trustworthy —
a YMYL ("Your Money or Your Life") health site where credibility is the whole
game.

This repo holds two kinds of source-of-truth, kept separate on purpose:

- **WHAT we're building** — the content, information architecture, conversion
  funnel, e-commerce, trust/SEO, and legal/compliance blueprint:
  **`docs/research/`**.
- **HOW we build it** — the phased engineering methodology (scaffold → shell →
  canvas → scenes → animation → CMS → form → optimize → SEO → deploy):
  **`docs/phases/`** + **`docs/00_MASTER_PROJECT.md`**.

> Implementation happens phase by phase; this repo currently holds the structure
> standard, the build methodology, and the content/IA blueprint.

## Start here

- **`docs/research/`** — the project's content brief: full sitemap, conversion
  funnel, digital-product e-commerce, trust/credibility, SEO, and the US
  legal/compliance requirements for a health practice.
- **`docs/00_MASTER_PROJECT.md`** — the engineering brief: the stack and the one
  architectural idea that governs the build (the *persistent canvas*).
- **`STRUCTURE.md`** — where every kind of file belongs and the conventions that
  keep it predictable.
- **`docs/phases/`** — per-phase working files (`PHASE_00` … `PHASE_12`).
- **`.cursor/rules`** — the Cursor project rules (role, stack, architecture).

## The core idea: one persistent canvas

The site mounts **one** React Three Fiber `<Canvas>` at the app-shell level that
persists across navigation. Pages don't create 3D — they declare what the single
canvas should show. This keeps any immersive/ambient visuals smooth without
remounting WebGL between pages. All 3D code lives in `src/canvas/`. See Phase 4.

> **Apply 3D with restraint here.** This is a calming health-conversion site, not
> a showreel: the blueprint calls for a warm, uncluttered, mobile-first feel and
> strong performance. Use ambient/subtle 3D where it supports calm, and never at
> the expense of the Lighthouse and accessibility targets (perf > 85 mobile,
> a11y = 100) or the trust signals that make a YMYL site convert.

## Stack

Next.js (App Router) + TypeScript · React Three Fiber + drei · Tailwind CSS ·
GSAP + ScrollTrigger · Lenis · Sanity (CMS) · react-hook-form + zod · Resend
(transactional email) · Vercel · pnpm. A digital-download e-commerce tool is
added per the blueprint (see `docs/research/`). Versions are pinned to latest
stable in Phase 1 — don't trust version numbers from memory.

## Routes

The five-route methodology skeleton (`/`, `/work`, `/work/[slug]`, `/about`,
`/contact`) is a starting point; the **canonical sitemap for this site** is the
blueprint in `docs/research/` — Home, About, How It Works, What We Help With +
per-problem landing pages, Shop / audio products / bundles / cart / checkout,
Resources / education / FAQ / testimonials, the discovery-call and free-audio
funnels, and the footer/legal pages (Privacy, Consumer Health Data Privacy,
Disclaimer, Scope of Practice, Accessibility, Cookies).

## Build order

Work the phases in order; each assumes the previous is complete. Feed the
`docs/research/` blueprint into Phase 2 (content model + sitemap) and onward. See
`docs/00_MASTER_PROJECT.md` and `docs/phases/README.md`.
