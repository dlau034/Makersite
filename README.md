# Strata One — Landing Page

A single-file, dependency-free marketing landing page for **Strata One**, a fictional desktop 3D printer. Built as a design study in what vanilla web tech can do with zero libraries and zero build step.

**Live:** https://makersite.vercel.app

> Strata® is a fictional brand — this page is a design study, not a real product.

## Highlights

- **One file, no dependencies.** Everything lives in [`index.html`](index.html) — HTML, CSS, and JS inline. No framework, no bundler, no `node_modules`. Opens from a double-click or any static host identically.
- **Every visual is code.** The 3D printer, the vase, gears, voxel cubes, film grain, and favicon are inline SVG / CSS — no image assets. Gear teeth are generated procedurally in JS.
- **Scroll-scrubbed print sequence.** The centerpiece "Process" section reveals a vase layer-by-layer as you scroll, driven by a lerped `requestAnimationFrame` loop for a physical feel.
- **Accessible & resilient.** Content works without JS (`.js`-gated animations), full `prefers-reduced-motion` fallback, ARIA labels, semantic landmarks, and visible focus states.
- **Performance-minded.** GPU-only transforms/opacity, passive scroll listeners, and `IntersectionObserver` reveals that unobserve after firing.

## Stack

| | |
|---|---|
| Markup / styling | Vanilla HTML + CSS (custom properties, fluid `clamp()` type) |
| Behavior | Vanilla JS (one IIFE, no libraries) |
| Fonts | Space Grotesk, Space Mono, Unbounded (Google Fonts) |
| Hosting | Vercel (static) |

## Run locally

The site is a static file, so any static server works. With Python:

```bash
python -m http.server 3000
```

Then open http://localhost:3000. Or simply double-click `index.html`.

## Deploy

Deployed to Vercel as a static site (no framework/build detected — it serves `index.html` directly):

```bash
vercel deploy --prod --yes --name makersite
```

## Structure

```
.
├── index.html        # the entire site — markup, styles, and scripts
├── README.md
├── CLAUDE.md         # guidance for AI coding assistants
└── .gitignore
```

## License

No license specified. This is a personal design study.
