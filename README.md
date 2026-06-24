# STRYV — Premium Sneaker Storefront

A single-page, six-section sneaker and apparel storefront. Vanilla HTML5 / CSS3 / JavaScript — zero frameworks, zero build step.

## Structure

```
index.html        — all 6 sections, header, modal, toast
css/style.css      — design tokens, layout, responsive breakpoints, RTL
js/i18n.js         — EN / FR / AR dictionary + language engine
js/products.js     — sneaker, category, and store data
js/main.js         — rendering, cart, modal, countdown, nav, scroll reveal
```

## Sections

1. **New Arrivals** — hero with animated gradient background (placeholder for video)
2. **Sneakers** — 3-product grid, opens quick-view modal with size + add-to-cart
3. **Collection** — 4 category tiles (Running, Lifestyle, Training, Football)
4. **Drops** — live countdown to next release + email notify form
5. **Commitments** — Sustainability / Performance / Community
6. **Stores** — Geneva, Lausanne, Zürich with live Google Maps links

## Features

- Functional cart (badge count, persisted in `localStorage`)
- Quick-view modal: focus-trapped, closes on Escape, restores focus on close
- Smart validation: can't add to cart without a size — toast + shake feedback
- Live countdown (days/hours/min/sec), target persisted in `localStorage`
- Trilingual: English, French, Arabic — auto-switches to RTL layout for Arabic, persisted across visits
- Mobile-first responsive: breakpoints at 480 / 768 / 1024 / 1280px, sneaker grid becomes a scroll-snap carousel on mobile
- Root-level `overflow-x: clip` prevents the off-screen mobile menu from stretching page width while keeping the sticky header intact

## Swapping in real visuals

- Hero background: replace `.hero__gradient` div in `index.html` with a `<video autoplay muted loop playsinline>` tag, point it at `assets/video/hero.mp4`, keep `.hero__noise` for grain.
- Product photography: replace the `sneakerSVG()` calls in `js/main.js` with `<img>` tags pointing to files in `assets/img/`.

## Deploy to Vercel

This is a static site — Vercel needs no build command or config.

### Option A — Vercel CLI (fastest)

```bash
npm install -g vercel       # if you don't have it
cd stryv
vercel                      # first deploy, follow prompts
vercel --prod               # promote to production
```

### Option B — Git + Vercel dashboard (auto-deploy on push)

```bash
cd stryv
git init
git add .
git commit -m "STRYV storefront"
git remote add origin <your-repo-url>
git push -u origin main
```

Then in the [Vercel dashboard](https://vercel.com/new): **Import Project** → select the repo → Framework Preset: **Other** → Deploy. No build command, no output directory override needed (root is served as-is).

Every subsequent `git push` auto-deploys.

## Notes

All product names, branding, and imagery are original/placeholder — no third-party trademarks.
