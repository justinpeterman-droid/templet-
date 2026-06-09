# templet-

An **immersive portfolio + marketing site** — a multi-page website that markets
and showcases work at once, built fully immersive (real-time 3D + cinematic
animation) while staying fast.

> This repository currently holds the **project structure standard and
> documentation scaffold**. Implementation happens phase by phase (see below).

## Start here

- **`docs/MASTER_BRIEF.md`** — the orienting brief: what we're building, the
  stack, and the one architectural idea that governs everything (the *persistent
  canvas*).
- **`STRUCTURE.md`** — the repository structure standard: where every kind of
  file belongs and the conventions that keep it predictable.
- **`docs/phases/`** — per-phase working files (`PHASE_00` … `PHASE_12`).
- **`.cursor/rules`** — the Cursor project rules (role, stack, architecture).

## The core idea: one persistent canvas

The site mounts **one** React Three Fiber `<Canvas>` at the app-shell level that
persists across navigation. Pages don't create 3D — they declare what the single
canvas should show. This is what lets every page feel immersive while still
loading fast. All 3D code lives in `src/canvas/`. See the brief, Phase 4.

## Stack

Next.js (App Router) + TypeScript · React Three Fiber + drei · Tailwind CSS ·
GSAP + ScrollTrigger · Lenis · Sanity · react-hook-form + zod · Resend · Vercel ·
pnpm. Versions are pinned to latest stable in Phase 1 — don't trust version
numbers from memory.

## Routes

`/` (home + hero scene) · `/work` · `/work/[slug]` · `/about` · `/contact`

## Build order

Work the phases in order; each assumes the previous is complete. See
`docs/MASTER_BRIEF.md` and `docs/phases/README.md`.
