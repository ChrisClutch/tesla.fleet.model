# Clutch Cybercab — site

Single static page. No build step, no dependencies beyond Google Fonts.

## Deploy to Cloudflare Pages via GitHub

1. Create a new GitHub repo (e.g. `clutch-cybercab`) and push these files to `main`.
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages → Connect to Git** → pick the repo.
3. Build settings: Framework preset **None**, build command **(leave blank)**, build output directory **/** (root).
4. Deploy. You'll get `https://<project>.pages.dev`; add a custom domain under **Custom domains** (e.g. `cybercab.clutchindustries.com`).

Every push to `main` redeploys automatically.

## Collecting waitlist submissions

The form works two ways:

- **Default (no setup):** submitting opens the visitor's email client with the form contents addressed to you.
- **Recommended:** create a free [Formspree](https://formspree.io) form (or a Cloudflare Worker), copy its endpoint URL, and paste it into `index.html` at `const FORM_ENDPOINT="";`. Submissions then post silently and you get them by email / dashboard.

## Editing the numbers

All calculator assumptions live in one object near the bottom of `index.html` (`const A={...}`): vehicle price, down payment, loan rate, fares, costs. The "own the depot" toggle switches parking to $600, charging to $0.14/kWh and cleaning to $1,200 per car.

## Files

- `index.html` — the whole site
- `_headers` — security headers for Cloudflare Pages
- `README.md` — this file
