# Design Direction — Hometown Serenity

The art-direction and homepage spec that feeds the first high-fidelity design
(Figma → tweak → pull → build). Derived from `docs/research/` and the owner's
brief. This is the *visual* source-of-truth; pair it with the IA/funnel/legal
content in `docs/research/`.

## Positioning

**A 50/50 blend of two models from the research:**
- **Local private practice** — warm, personal, grounded, 1:1 + a downloadable
  audio shop (InnerZension-style trust and low-friction entry).
- **Clinical / evidence-led** — calm authority, symptom-first navigation,
  research-backed credibility (Mindset Health-style trust).

One sentence: **"Web designer meets caring hypnotherapist."** Professional and
beautifully built, but unmistakably human and safe.

## Art direction: "Nature meets hippie Star Trek"

Organic, earthy calm **fused with** clean, luminous, hopeful sci-fi. Not cold,
not new-age-kitsch — *awe with warmth.*

- **Nature / hippie:** botanical forms, soft organic blobs and flowing gradients,
  grain/texture, natural light, hand-warm imperfection, plant/forest/water motifs.
- **Star Trek / luminous tech:** clean geometry, generous negative space, subtle
  depth and parallax, soft glow/aurora accents, confident structure, a sense of
  calm futurism and possibility.
- **3D, used with restraint:** tasteful ambient motion (a slow-breathing
  organic-luminous form in the hero, gentle parallax depth), never busy or
  high-arousal. It must *lower* the nervous system, per the research's 50ms
  trust rule — calm first, wow second.

## Palette (calming, research-driven; verify AA in Figma)

| Role | Direction |
|------|-----------|
| Background base | warm off-white / cream (avoid sterile pure white) |
| Surface / depth | very soft desaturated sage-green + soft blue washes |
| Primary calm | desaturated soft **blue** (focus, lowered heart rate) |
| Growth / nature | desaturated **green** (renewal, habit-change) |
| Luminous accent | a single bioluminescent **teal/aurora** glow — used sparingly for the primary CTA and 3D light |
| Text / ink | deep desaturated slate/ink (high contrast on cream, **AA/AAA**) |

Avoid: neon, stark high-contrast, vivid purple, large sterile white voids, more
than one loud accent.

## Typography (from the research's pairings)

- **Recommended:** Display = a soft, organic-warm face (**Fraunces** soft-serif
  *or* **Poppins** rounded geometric) for the "nature/human" feel; Body/UI =
  **DM Sans** (or **Karla**) for clinical clarity and low cognitive load.
- Pick **one** display + **one** body. Load via `next/font`. Keep body ≥16px,
  generous line-height, short measure for distressed readers.

## 3D / motion guardrails (non-negotiable)

- Respect `prefers-reduced-motion`: ship a calm static variant.
- Mobile + low-power fallback (static poster / reduced detail); never block first
  paint — lazy-load + Suspense.
- Hold the targets: **Lighthouse perf > 85 mobile, a11y = 100.** 3D never wins
  over trust, readability, or SEO.
- Canvas is decorative (`aria-hidden`); all content is real, semantic DOM.

## Homepage section spec (what the Figma draft will contain)

1. **Hero** — calm luminous-organic 3D backdrop; H1 outcome/problem headline;
   reassuring subhead; **one** dominant CTA **"Book a Free Discovery Call"**;
   secondary **"Listen to a free track"**; a micro-trust line (credential /
   association). *(See open decision: free call vs. nominal paid deposit.)*
2. **Reassurance / "What it is — and isn't"** — short destigmatizing line
   ("meditation with a goal"), normalizing trance, you're always in control.
3. **What we help with** — problem-first cards (Anxiety, Sleep, Confidence,
   Smoking, Weight, Habits…) each linking to its landing page + CTA.
4. **How it works** — 3 calm steps (Discovery call → Sessions → Outcomes).
5. **Evidence band** — credibility row: association badges + a couple of
   carefully-qualified, cited research points (clinical-model trust).
6. **Audio shop teaser** — a few featured downloadable tracks/bundles → shop.
7. **About teaser** — real photo of the practitioner + a human one-liner → About.
8. **Testimonials** — social proof *with* the required disclaimer (results vary).
9. **Final CTA band** — repeat "Book a Free Discovery Call."
10. **Footer** — nav, legal links (Privacy, **Consumer Health Data Privacy**,
    Disclaimer, Scope of Practice, Accessibility, Cookies), NAP/contact, and a
    **crisis line (988)** safety note.

## Open decisions that change final copy/design (need owner input)

- **Jurisdiction / states served** → drives the legal/footer pages.
- **Practitioner credentials & licensure** (NGH/ASCH/SCEH? licensed clinician?)
  → drives the trust/evidence band.
- **Free discovery call vs. nominal paid deposit** → hero CTA + funnel.
- **Audio e-commerce tool** (Next.js-compatible: Stripe + custom delivery,
  Lemon Squeezy, Snipcart, Payhip/Gumroad embeds) — *not* WordPress's Easy
  Digital Downloads, which the research recommends but doesn't fit our stack.

These don't block a first visual draft (we'll use sensible placeholders), but
they sharpen it.
