# Deployment Notes — greenoso.github.io

This is a customized fork of [al-folio](https://github.com/alshedivat/al-folio) for **Jiacheng Liu**'s personal academic website.

## What's already configured

- `_config.yml` — name, description, url=`https://greenoso.github.io`, baseurl empty (personal site), keywords.
- `_pages/about.md` — bio, MBZUAI affiliation, advisor, Huawei internship, recent papers. News/announcements & latest_posts disabled.
- `_data/socials.yml` — email, GitHub `Greenoso`, Google Scholar id `_awln6YAAAAJ`. RSS disabled.
- `_bibliography/papers.bib` — replaced with 5 real papers (BiGain, Next-Gen CAPTCHAs, CaptchaWorld, FADRM, Pangu-Agent). BiGain & Next-Gen CAPTCHAs are flagged `selected={true}` so they appear on About page.
- Navbar trimmed: only **about** + **publications**. CV / Projects / Blog / Repositories / Teaching / Profiles all set to `nav: false`.

## What you must do before pushing

1. **Replace profile photo.** Drop your headshot at `assets/img/prof_pic.jpg` (overwrite Einstein). Square JPG ≥ 400×400 ideal.
2. **(Optional) Verify advisor URL.** In `_pages/about.md` I linked `https://zhiqiangshen.com/` — change if wrong.
3. **(Optional) Verify Kun Shao Scholar URL.** Same file links `https://scholar.google.com/citations?user=Y7s8VTAAAAAJ` — replace if not the correct profile.

## How to deploy to GitHub Pages

**Note:** `Greenoso/Greenoso.github.io` already exists (currently only a README). We'll replace its contents while keeping the repo's git history.

### One-time setup (on your local machine, not this server)

```bash
# 1. Pull this folder down from the server
scp -r jiachengl@<server>:/data/spiderman/jiachengl/draft/intern/website ./greenoso-site

# 2. Drop al-folio's bundled .git
cd greenoso-site
rm -rf .git

# 3. Get your existing Greenoso.github.io repo's .git
cd ..
git clone git@github.com:Greenoso/Greenoso.github.io.git existing-repo
mv existing-repo/.git greenoso-site/

# 4. Commit and push
cd greenoso-site
git add .
git commit -m "Replace placeholder with al-folio personal site"
git push origin main

# 5. On GitHub: Settings → Pages → Source = "GitHub Actions"
#    (al-folio ships its own .github/workflows/deploy.yml — auto-builds on push.)
```

Site will be live at `https://greenoso.github.io/` after the first GH Actions run finishes (≈ 2 minutes).

### Local preview (optional, recommended)

Easiest path is Docker (al-folio ships a `docker-compose.yml`):

```bash
docker compose pull && docker compose up
# open http://localhost:8080
```

If no Docker, install Ruby 3.x + Bundler then:

```bash
bundle install
bundle exec jekyll serve --livereload
# open http://localhost:4000
```

## Iterating later

- **Add a paper:** append a BibTeX entry to `_bibliography/papers.bib`. Set `selected={true}` to also show on About page.
- **Update bio:** edit `_pages/about.md`.
- **Re-enable a page:** flip `nav: false` → `nav: true` in the `_pages/*.md` frontmatter.
- After any change: `git commit + push` → GH Actions rebuilds.

## Notes / decisions baked in

- **CV page disabled** per user's choice (CV not on website).
- **News / announcements / latest_posts disabled** to keep the About page clean.
- **Selected papers** = BiGain (CVPR'26 first-author) + Next-Gen CAPTCHAs (arXiv first-author).
- Keep the `LICENSE` file (al-folio is MIT, attribution lives in the footer text).
