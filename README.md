# Personal Academic Website — Erez Zimmerman

A clean, professional static site for postdoc applications, built with [Jekyll](https://jekyllrb.com/) and deployable to [GitHub Pages](https://pages.github.com/).

---

## Local development

### Prerequisites

- Ruby ≥ 3.1 and Bundler: `gem install bundler`
- (macOS) Install via Homebrew: `brew install ruby` then follow the PATH instructions

### Setup

```bash
cd website/
bundle install
```

### Run locally

```bash
bundle exec jekyll serve --livereload
```

Open http://localhost:4000 in your browser. The site rebuilds automatically on file changes.

---

## GitHub Pages deployment

### Option A — User/org site (recommended)

1. Create a GitHub repo named **`<your-username>.github.io`**
2. Push this directory to the `main` branch
3. In repo **Settings → Pages**, set source to `main` branch, root `/`
4. Update `_config.yml`: set `url` to `https://<your-username>.github.io` and `baseurl` to `""`
5. Your site will be live at `https://<your-username>.github.io` within ~2 minutes

### Option B — Project site

1. Create any GitHub repo (e.g. `website`)
2. Push this directory to `main`
3. In repo **Settings → Pages**, set source to `main`, root `/`
4. Update `_config.yml`: set `url` to `https://<your-username>.github.io` and `baseurl` to `/website`
5. Site lives at `https://<your-username>.github.io/website`

---

## Filling in your content

All TODOs are marked with `TODO:` in the source files. Here's the quick-start checklist:

### High priority

- [ ] **`_config.yml`** — update `url`, `baseurl`, and all `author:` fields (GitHub, ORCID, ADS, Scholar)
- [ ] **`index.html`** — replace bio text with your own 2–3 sentence intro
- [ ] **`assets/img/photo.jpg`** — add your headshot (square crop, ≥400×400 px), then uncomment the `<img>` in `index.html`
- [ ] **`_data/publications.yml`** — add your real papers (bold your name with `**Your Name**`)
- [ ] **`assets/cv.pdf`** — replace with the current CV; the nav links to it directly

### Per-page

| File | What to update |
|------|---------------|
| `research/index.html` | Research theme titles, descriptions, and figures |
| `_data/outreach.yml` | Outreach items and press links |

### Adding a figure

1. Save the image to `assets/img/` (e.g. `research-spectra.png`)
2. In the relevant HTML, replace the `<figure class="theme-fig">` contents with:
   ```html
   <img src="{{ '/assets/img/research-spectra.png' | relative_url }}"
        alt="Brief description" />
   ```

---

## Project structure

```
website/
├── _config.yml          # Site settings, author links, keywords
├── Gemfile              # Ruby gem dependencies
├── index.html           # Home page
├── 404.html             # Not-found page
├── _layouts/
│   ├── default.html     # Base HTML shell (nav + footer)
│   └── page.html        # Inner page layout (page hero + content area)
├── _includes/
│   └── footer.html      # Footer with social links
├── _data/
│   ├── publications.yml # Publication list
│   ├── outreach.yml     # Outreach, media, press
│   └── software.yml     # Project descriptions
├── assets/
│   ├── css/main.css     # All styles (single file, no preprocessor required)
│   ├── img/             # Photos, figures, screenshots
├── research/index.html
├── publications/index.html
├── outreach/index.html
└── assets/cv.pdf        # CV (linked directly from the nav)
```

---

## Customization tips

**Change the accent color** — edit `--accent` in `assets/css/main.css` (line ~8).

**Add a new page** — create `newpage/index.html` with `layout: page` in the front matter, then add a link in `_layouts/page.html` and `index.html`.

**Update publications easily** — only edit `_data/publications.yml`; no HTML changes needed.

**Custom domain** — add a `CNAME` file at the repo root containing your domain (e.g. `www.yourdomain.com`), then configure your DNS provider.
