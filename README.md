# AEW Automotive — New Website

Static site rebuild for AEW Automotive Service and Repair (Leander, TX).
Plain HTML/CSS/JS, no framework, no build step, no backend.

## Repo layout

```
.
├── site/                 <- deployable website (this is the Cloudflare Pages build output directory)
│   ├── index.html
│   ├── services.html
│   └── assets/
│       └── aew-logo.png
├── assets/               <- source brand assets (not deployed)
├── research/             <- internal planning docs, NOT deployed (keep this repo private if it must stay tracked)
├── HANDOFF.md            <- internal build handoff notes, NOT deployed
└── README.md             <- this file
```

Only the contents of `site/` are served to the public. Everything else
(`research/`, `HANDOFF.md`, root `assets/`) is project documentation that
lives in the repo but is excluded from the published site by pointing
Cloudflare Pages at the `site/` subdirectory (see below) rather than the
repo root.

If this repo is public, be aware `research/` contains an internal client
proposal PDF and planning notes — move it out of git history or make the
repo private if that shouldn't be publicly visible on GitHub.

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

## Updating content

Edit `site/index.html` / `site/services.html` directly (styles and scripts
are embedded in each file, self-contained). Known placeholders still
needing real content from the client are marked inline as HTML comments
(`<!-- PLACEHOLDER: ... -->`) — see `HANDOFF.md` for the full list.
# austineuroworks
