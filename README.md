# AEW Automotive — New Website

[View Site](/site)

Static site rebuild for AEW Automotive Service and Repair (Leander, TX).
Plain HTML/CSS/JS, no framework, no build step, no backend.

## Deploying on Cloudflare Pages

1. Push this repo to GitHub.
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages → Connect to Git**, pick this repo.
3. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty — there is no build step)*
   - **Build output directory:** `site`
   - **Root directory:** `/` (default)
4. Deploy. Cloudflare will serve `site/index.html` and `site/services.html`
   directly, with `site/assets/aew-logo.png` resolving via the existing
   relative paths in both pages — no path changes needed.
5. Every push to the connected branch triggers a new deploy automatically.
   No environment variables, secrets, or functions are required — this is
   a 100% static site.
