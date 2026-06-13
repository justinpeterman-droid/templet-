# Reference

Third-party **technical reference** material — distinct from `docs/research/`
(our content/IA brief for the hypnotherapy site) and `docs/phases/` (our build
methodology). Things here are vendored copies of external code/docs we learn
from while building; they are not our application code.

## `react-three-next.repomix.md`

A [Repomix](https://repomix.com) pack of the official Poimandres starter
**[pmndrs/react-three-next](https://github.com/pmndrs/react-three-next)** —
the entire starter codebase merged into one readable / LLM-ingestible file.

| | |
|---|---|
| **Upstream** | https://github.com/pmndrs/react-three-next (branch `main`) |
| **License** | MIT (upstream) — this is upstream's code, packed verbatim |
| **Generated** | 2026-06-09 |
| **Command** | `npx --yes repomix@latest --remote https://github.com/pmndrs/react-three-next --style markdown --output docs/reference/react-three-next.repomix.md` |
| **Contents** | 36 files, ~10.7k tokens. Binary assets (`public/dog.glb`, `public/duck.glb`) excluded by repomix; Repomix security scan found nothing suspicious. |

### Why it's here

This starter is the canonical implementation of the **persistent-canvas
architecture** our Phase 4 (`docs/phases/PHASE_04_PERSISTENT_CANVAS.md`)
describes: one `<Canvas>` that survives navigation, with pages declaring *what to
show* rather than mounting their own 3D. It does this with drei's **`View`**
component plus **`tunnel-rat`** — DOM elements mark where 3D should appear, and a
single canvas renders each tracked view. Keep this pack handy while building
Phase 1 (scaffold) and Phase 4 (the keystone).

### Map of the key files inside the pack

(The starter uses the **Next.js App Router**.)

- `app/layout.jsx` — root layout; where the global DOM + canvas wrapper mount.
- `src/components/dom/Layout.jsx` — wraps page content and hosts the single canvas.
- `src/components/canvas/Scene.jsx` — the **one persistent `<Canvas>`** (+ `Preload`, event source).
- `src/components/canvas/View.jsx` — the **`View`** wrapper (drei `View as ViewImpl`) that tracks a DOM node and tells the canvas to render a scene there.
- `src/helpers/components/Three.jsx` — the **tunnel** (`tunnel-rat`) bridging DOM-side `<View>` children into the canvas.
- `src/components/canvas/Examples.jsx` — example meshes/scenes (the swappable "what to show").
- `app/page.jsx`, `app/blob/page.jsx` — example routes wiring views to pages.
- `src/templates/` — reusable bits: `Shader/` (glsl frag/vert + material), `Scroll.jsx`, `hooks/usePostprocess.jsx`.
- `next.config.js`, `tailwind.config.js`, `package.json` — stack & config to mine for versions and transpile/glsl setup.

> ⚠️ Treat the pack as **read-only**. To refresh it, re-run the command above; it
> will re-pull `main` and overwrite this file.
