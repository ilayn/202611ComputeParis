# BLAS talk

Slides built with [Slidev](https://sli.dev). Requires Node >= 22.22.

```sh
npm install
npm run dev      # live preview at http://localhost:3030 (presenter view at /presenter)
npm run build    # static site in dist/
npm run export   # PDF fallback (first run asks you to install playwright-chromium)
```

- `slides.md` holds the deck
- `components/` holds Vue components, auto-imported into slides
- `public/` holds static assets, served from `/` (e.g. `public/figures/x.svg` becomes `/figures/x.svg`)
