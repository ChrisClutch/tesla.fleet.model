# Salem Fiscal Compact — website

Static site (plain HTML + CSS, no build step). Hosts anywhere; built for GitHub + Cloudflare Pages.

## Files

| File | What it is |
|---|---|
| `index.html` | Landing page — the loop, the five rules, the accountability rider, sign-on form |
| `compact.html` | The printable one-pager (has a Print / Save-as-PDF button) |
| `who-runs-salem.html` | Council-manager civics explainer |
| `faq.html` | Frequently asked questions |
| `styles.css` | All styling |
| `favicon.svg` | Icon |
| `404.html` | Cloudflare Pages picks this up automatically for missing pages |
| `_headers` | Security headers (Cloudflare Pages reads this file) |
| `robots.txt` | Lets search engines index everything |

## Deploy in 5 minutes

**1. Put it on GitHub**

```bash
cd salem-fiscal-compact
git init
git add .
git commit -m "Salem Fiscal Compact site"
# create an empty repo on github.com (e.g. salem-fiscal-compact), then:
git remote add origin https://github.com/YOUR_USER/salem-fiscal-compact.git
git branch -M main
git push -u origin main
```

**2. Connect Cloudflare Pages**

1. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Pick the repo.
3. Build settings: Framework preset **None**, build command **(leave empty)**, build output directory **/** (root).
4. Save and Deploy. You'll get a `*.pages.dev` URL in about a minute.

**3. Custom domain (optional)**

Pages project → **Custom domains** → add `salemfiscalcompact.org` (or whatever you buy). If the domain's DNS is already on Cloudflare it's one click; otherwise add the CNAME they show you.

Every `git push` to `main` redeploys automatically.

## Make the sign-on form work

The form on `index.html` posts to a placeholder. Pick one:

**Option A — Formspree (fastest, free tier ~50 submissions/month).**
Create a form at formspree.io, copy the endpoint, and replace `https://formspree.io/f/YOUR_FORM_ID` in `index.html`. Done.

**Option B — Cloudflare Pages Function (free, unlimited, keeps data in your account).**
Create `functions/api/sign.js` that reads the POST body and writes to a Cloudflare KV namespace or D1 database, then change the form `action` to `/api/sign`. Cloudflare's docs: "Pages Functions" → "Get started".

**Option C — No form.** Delete the `<form>` block and replace it with a `mailto:` link.

## Editing

Everything is plain HTML. The five rules appear in two places — `index.html` (cards) and `compact.html` (full text) — so change both if you edit the wording. The nav and footer are copied into each page; edit all four if you add a page.

## Before you go live — checklist

- [ ] Replace the Formspree ID (or pick option B/C above)
- [ ] Confirm the 2023 payroll-tax reference matches how you want to describe it
- [ ] Decide whether to link councilor contact info directly (currently links to cityofsalem.net home)
- [ ] Add an Open Graph image (`og:image`) if you want a preview card on social — a 1200×630 PNG works
- [ ] Add analytics if wanted (Cloudflare Web Analytics is free and needs no cookie banner: Pages project → Metrics → enable)
