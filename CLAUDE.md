# electricautonomy.com

Read this first. It explains what this site is, how it is built and published,
and how the owner wants to work, so any new chat can continue the work.

## About the site

- **What it is:** the website for **electricautonomy.com**. It is a new site,
  separate from **electricautonomy.ca**. Don't copy that site's content or
  link the two unless the owner asks.
- **What it does:** a simple one-page site that showcases Electric Autonomy
  and links to all of its other work.
- **Owner:** not a developer. Explain everything in plain language.
- **Sister site:** `arcascent/arcascent-website` (arcascent.com) uses the
  same kind of setup (plain HTML on GitHub Pages with a `CNAME` file) and is a
  useful reference.

## How the owner wants to work

1. **Never push to `main`** unless the owner says **"publish"**. Make every
   change on a new branch and open a pull request (PR) for review.
2. **Screenshots before publishing:** for every visible change, send the owner
   screenshots on **desktop** and **mobile** (see "Screenshots" below).
3. **When the owner says "publish":** merge the PR into `main`, wait for the
   live site to update, then load the live page and confirm the change is
   there. Send a screenshot of the live page as proof.
4. **Plain language.** Avoid jargon. If you have to use a technical term,
   explain it in a few words.
5. **Ask before guessing.** If anything is unclear (content, links, wording,
   design), ask. Don't invent copy, links, logos or facts about the company.
6. **Steps outside GitHub:** when the owner has to do something outside
   GitHub (Cloudflare DNS, GitHub settings, accounts), give exact,
   numbered, click-by-click steps.

## How the site is built

- **Plain HTML and CSS. No build step, no framework, no npm.** The page you
  edit is the page that goes live.
- Files (kept at the top level of the repo):
  - `index.html` – the one page: a carbon-texture header with the EA logo
    and intro, a two-column grid of program cards (photo, logo plate,
    headline, blurb, "Learn more"), a "Talk to our team" band, and a footer
    (copyright line plus Privacy Policy and Terms & Conditions links to
    electricautonomy.ca, as the owner asked). The footer year updates
    automatically via a one-line script; "2026" is written in as a fallback.
  - `styles.css` – all styling (fonts: Inter, Space Grotesk, Montserrat from
    Google Fonts; gold accent #FFC20D)
  - `assets/logos/` – program logos; `assets/photos/` – card photos and the
    carbon background (resize new photos to ~1200 px wide before adding)
  - `CNAME` – contains just `electricautonomy.com` (tells GitHub Pages
    the domain)
- Keep it simple, fast and accessible: one page, works well on phones,
  real text (not text in images), alt text on images, good colour contrast.
- To preview locally: `python3 -m http.server 8000` from the repo root, then
  open http://localhost:8000.

## How the site is published

- **Hosting:** GitHub Pages, set to "Deploy from a branch" → `main` →
  `/ (root)`. Every merge to `main` updates the live site automatically,
  usually within 1–2 minutes. (GitHub runs a "pages build and deployment"
  workflow, which you can check in the repo's Actions tab.)
- **Domain/DNS:** electricautonomy.com is managed in **Cloudflare**. DNS
  records for GitHub Pages:
  - `A` records for `electricautonomy.com` (name `@`): `185.199.108.153`,
    `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
  - `AAAA` records for `@` (optional, IPv6): `2606:50c0:8000::153`,
    `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
  - `CNAME` record `www` → `arcascent.github.io`
  - Set the proxy status to **DNS only (grey cloud)** so GitHub can issue
    the free HTTPS certificate. Then tick "Enforce HTTPS" in the repo's
    Settings → Pages.
  - Before changing DNS, check what records already exist. **Never touch
    email records (MX, TXT for SPF/DKIM/DMARC).**
- **Cost:** free. GitHub Pages is free for **public** repos, and this repo is
  public. Never commit passwords, keys or private documents: anyone can read
  the repo.

## Day-to-day workflow (for Claude)

1. Create a branch from the latest `main` (e.g. `update-links`).
2. Make the change and preview it locally.
3. Take screenshots (below) and send them to the owner.
4. Push the branch and open a PR with a plain-language description of the
   change.
5. Wait. Only when the owner says **"publish"**: merge the PR, watch the
   Pages deployment finish, load https://electricautonomy.com (bypass the
   cache, e.g. add `?v=<timestamp>`), confirm the change, and send a
   screenshot of the live page.

### Screenshots

Use the pre-installed Playwright/Chromium against the local preview server:

- Desktop: viewport 1440×900, `deviceScaleFactor: 2`, full page
- Mobile: Playwright device `iPhone 13` (don't set a scale factor), full page

Save them outside the repo (don't commit screenshots) and send them to the
owner with a short caption saying what changed.

## Current status / to-do

Update this section whenever something changes.

- [x] Repo created (`arcascent/electricautonomy.com`)
- [x] CLAUDE.md added
- [x] Hosting decided: **make the repo public** and use free GitHub Pages
      (owner changes the visibility in GitHub settings)
- [x] One-page site built (`index.html`, `styles.css`, `assets/`) from the
      owner's Claude Design mockup "electricautonomy.com homepage"
      (https://claude.ai/artifact/2bVm1YnPUBQqoErCJT6zMp, artboard
      "Homepage — desktop"). Photos were resized for the web.
- [x] `CNAME` file added
- [x] Real links added for all 8 cards (Webinars → the Electric Autonomy
      YouTube channel) and the "Talk to our team" button
      (→ https://electricautonomy.ca/advertise/), as given by the owner
- Owner rule: **every link opens in a new tab** (`target="_blank"
  rel="noopener"`). Keep this for any link you add.
- [x] Repo made public (owner did this on 2026-11-14)
- [ ] GitHub Pages turned on (Settings → Pages → Deploy from a branch →
      `main` / root). Do this at the first "publish", after the PR is merged.
- [ ] Owner updates Cloudflare DNS (step-by-step instructions to be provided)
- [ ] Turn on "Enforce HTTPS" once the certificate is issued
- [ ] Confirm https://electricautonomy.com and https://www.electricautonomy.com
      both load the site
