# Repository Structure Standard

This document is the **single source of truth for where things live** in this
project. `docs/research/` is the **content/IA brief** (*what* we are building — the
Hometown Serenity hypnotherapy practice site); `docs/00_MASTER_PROJECT.md` is the
**engineering brief** (the stack and the persistent-canvas idea — *how* we build);
and this file defines *where* each kind of file belongs and the conventions that
keep the codebase predictable as it grows through the phases.

> The directory skeleton below is committed up front (with `.gitkeep` placeholders)
> so every phase drops its output into a known location instead of inventing one.

## Top-level layout

```
templet-/
├── .cursor/
│   └── rules                  # Cursor project rules (role, stack, architecture)
├── docs/                      # Project documentation
│   ├── 00_MASTER_PROJECT.md   # Engineering brief — keep open while working
│   ├── research/              # Content/IA brief (the hypnotherapy site spec)
│   ├── reference/             # Third-party technical reference (e.g. repomix packs)
│   └── phases/                # PHASE_00 … PHASE_12 working files
├── public/                    # Static assets served as-is
│   ├── models/                # glTF/Draco 3D models (lazy-loaded)
│   └── images/                # Raster/vector images (served via next/image)
├── scripts/                   # One-off & build/maintenance scripts
├── src/
│   ├── app/                   # Next.js App Router — routes, layouts, metadata
│   │   ├── work/              # /work index
│   │   │   └── [slug]/        # /work/[slug] detail (generated from CMS)
│   │   ├── about/             # /about
│   │   ├── contact/           # /contact (form lives here)
│   │   └── api/               # Route handlers (e.g. contact form → Resend)
│   ├── canvas/                # The ONE persistent R3F canvas + everything 3D
│   │   └── scenes/            # Per-page scene definitions the canvas swaps in
│   ├── components/            # Reusable React components (non-3D)
│   │   ├── layout/            # Shell: nav, footer, page frames
│   │   └── ui/                # Buttons, inputs, primitives
│   ├── lib/                   # Framework-agnostic utilities, hooks, clients
│   ├── sanity/                # CMS: schemas, client, queries
│   │   └── schemas/           # Sanity document/object schemas
│   └── styles/                # Tailwind layer files, global CSS, design tokens
└── tests/                     # Tests (unit / integration / e2e)
```

## Where each phase's output lands

| Phase | Produces | Primary location |
|-------|----------|------------------|
| 0 Foundation | Tooling, Cursor rules, Git | repo root, `.cursor/` |
| 1 Scaffold | Wired Next.js app | `src/app/`, config at root |
| 2 UX Architecture | Tokens, content model, a11y baseline | `src/styles/`, `src/sanity/schemas/`, `docs/` |
| 3 Shell | Nav, layouts, 5 routes | `src/components/layout/`, `src/app/**` |
| 4 Persistent Canvas | The single canvas (keystone) | `src/canvas/` |
| 5 Hero Scene | First scene + scene pattern | `src/canvas/scenes/` |
| 6 Animation | Scroll/transition/micro-interactions | `src/lib/` (hooks), `src/canvas/` |
| 7 CMS | Sanity wired in | `src/sanity/` |
| 8 Contact Form | Validated form + email | `src/app/contact/`, `src/app/api/` |
| 9 Optimization | Responsive/a11y/perf tuning | cross-cutting |
| 10 SEO/Analytics | Metadata, social, analytics | `src/app/**` metadata, `src/lib/` |
| 11 Deployment | Vercel + domain + env | root config, `vercel.json` |
| 12 Handoff | Maintenance docs | `docs/` |

## Conventions

- **The persistent canvas is sacred.** All 3D code lives under `src/canvas/`.
  Pages NEVER mount their own `<Canvas>` — they declare what to show via shared
  state/context that the single canvas reads. (See Phase 4.)
- **Routes own their metadata.** Each route in `src/app/**` exports `metadata`
  (or `generateMetadata`) for SEO. No route ships without it.
- **Components are small and single-purpose.** Prefer composition over large
  files. Non-3D reusable UI → `src/components/`; 3D → `src/canvas/`.
- **Assets:** images go through `next/image` from `public/images/`; 3D models are
  glTF + Draco in `public/models/` and are lazy-loaded.
- **Co-locate by concern, not by type, inside a feature** when a component grows
  its own styles/tests/helpers; otherwise use the shared folders above.
- **`docs/` is the project's memory.** Decisions, the brief, and per-phase notes
  live here so the reasoning survives across phases. `docs/reference/` holds
  vendored third-party technical reference (e.g. Repomix packs of starters we
  learn from) — read-only, not our application code.

## Naming

- Directories: `kebab-case`. React components: `PascalCase.tsx`.
- Hooks: `useThing.ts`. Utilities: `camelCase.ts`. Sanity schemas: `thing.ts`.
- Route segments follow Next.js App Router conventions (`page.tsx`,
  `layout.tsx`, `loading.tsx`, `route.ts`).
