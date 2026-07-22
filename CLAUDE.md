# CLAUDE.md

Guidance for AI coding assistants working in this repository.

## What this is

A **single-file marketing landing page** for *Strata One*, a fictional desktop 3D printer. It is a design study — there is no backend, no product, and no real reservation flow. All CTAs are anchor links or a UI toast.

The entire site is [`index.html`](index.html) (~1,240 lines): inline HTML, CSS, and JS. There is **no build step, no package manager, and no dependencies**. Do not introduce a framework, bundler, or `node_modules` unless explicitly asked — the zero-dependency, single-file nature is the point of the project.

## Working in this repo

- **Edit `index.html` directly.** Styles live in the `<style>` block in `<head>`; behavior lives in the single IIFE `<script>` at the end of `<body>`.
- **Every visual is code** — inline SVG and CSS, no image files. When adding graphics, keep them inline SVG/CSS rather than fetching assets, and animate with GPU-friendly `transform`/`opacity` only.
- **Match the existing style:** compact, comment-sectioned CSS (`/* ===== section ===== */`), design tokens as CSS custom properties in `:root`, fluid `clamp()`-based sizing, and terse vanilla JS (no libraries).

## Things to preserve

- **No-JS fallback:** animations are gated behind the `.js` class added at the top of `<body>`. Content must remain visible without JS.
- **Reduced motion:** there is a full `@media (prefers-reduced-motion: reduce)` block and a `reduced` branch in the JS. Any new motion should honor both.
- **Accessibility:** keep ARIA labels, semantic landmarks, and `:focus-visible` styles intact.
- **Burger menu ⇄ X animation:** the three `.menu-btn span` lines collapse into an X on `body.menu-open`. The `translateY` offsets in the open state must equal the resting center-to-center spacing of the lines, which is derived from the button's `height`, `padding-block`, and `gap`. If you change any of those, recompute and update the `translateY` values so the X still converges cleanly.

## Local dev

Any static server works; the file also runs from a double-click.

```bash
python -m http.server 3000   # then open http://localhost:3000
```

## Deploy

Hosted on Vercel as a static site (no framework/build). Project name is `makersite` (lowercase required by Vercel).

```bash
vercel deploy --prod --yes --name makersite
```

Note: the Vercel deploy is CLI-based and **not** git-connected, so pushing to GitHub does not auto-redeploy — run the deploy command after pushing.
