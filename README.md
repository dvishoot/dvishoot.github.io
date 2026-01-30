# Daniel Vishoot — Hugo Blog (PaperMod Custom)

This repo is a Hugo site using the PaperMod theme with a custom rail‑first layout, palette switcher, and a minimalist series system. It is designed to be **recruiter‑friendly** (fast to scan, text‑forward, low‑clutter) while still carrying a distinctive aesthetic.

## Quick Start

```sh
hugo server --disableFastRender -D
```

- `-D` shows draft posts
- `--disableFastRender` avoids stale caching during editing

## Content Authoring (Out‑of‑the‑Box)

### Create a post

Engineering:
```sh
hugo new posts/engineering/my-post/index.md
```

Adventures:
```sh
hugo new posts/adventures/my-trip/index.md
```

This uses `archetypes/posts.md` and automatically sets:
- `categories` (engineering/adventures)
- `series = []`
- `tags = []`

### Drafts and publishing
- New posts default to `draft = true`.
- Set `draft = false` to publish.

### Summaries
Auto‑summaries are enabled.
- If you want manual control, add `<!--more-->` in the markdown.
- Everything above `<!--more-->` becomes the summary.

### Tags
Add as needed:
```toml
tags = ["systems", "performance", "linux"]
```

### Series (multi‑part posts)
To add a post to a series:
```toml
series = ["Latency Logs"]
```

Rules:
- A series only appears when **2+ posts** share the same series name.
- Series ordering is by `date` (includes time). Use distinct timestamps for deterministic order.
- Series is scoped to the current section, so Engineering and Adventures never mix.

Optional:
Create a series landing page for richer descriptions:
```
content/series/latency-logs/_index.md
```

## Site Features

- **Rail‑first navigation** with palette switcher and dark mode toggle.
- **Palette switching** stored in localStorage (`pref-palette`).
- **Series UI**:
  - Subtle line under post title: `Series: X · Part N of M`
  - Previous/Next within the series in the footer
  - Series list on section pages (Engineering / Adventures)
- **Reply link**: posts include a minimal “Reply” link to `/about/#contact`.

## Assets & Fonts

Fonts are self‑hosted for privacy and speed:
- Font files live in `static/fonts/`
- `layouts/partials/fonts.html` declares all `@font-face` rules.

**If changing fonts**:
1. Replace files in `static/fonts/`
2. Update `layouts/partials/fonts.html`

## Avatars

Place your avatar at:
```
static/img/avatar.png
```

It will appear:
- In the rail header (desktop)
- At the top of the About page (via shortcode)

## Theme Updates (PaperMod)

PaperMod is a git submodule:
```
themes/PaperMod
```

**Update process**
1. Update the submodule:
   ```sh
   git submodule update --remote --merge
   ```
2. Diff your overrides against upstream:
   ```sh
   diff -u themes/PaperMod/layouts/_default/single.html layouts/_default/single.html
   diff -u themes/PaperMod/layouts/_default/list.html layouts/_default/list.html
   diff -u themes/PaperMod/layouts/partials/header.html layouts/partials/header.html
   diff -u themes/PaperMod/layouts/partials/footer.html layouts/partials/footer.html
   ```
3. Manually merge upstream improvements you want to keep.

**Override files (custom UX)**
- `layouts/_default/single.html` (series line + series nav + reply link)
- `layouts/_default/list.html` (series section above lists)
- `layouts/partials/header.html` (rail layout)
- `layouts/partials/footer.html`
- `layouts/partials/home_hero.html`
- `assets/css/extended/custom.css`

## Deployment Notes

- Hugo outputs to `public/` (ignored via `.gitignore`).
- GitHub Pages deployment is handled via `.github/workflows/hugo.yaml`:
  - On every push to `main`, GitHub Actions builds the site and publishes `public/` to the `gh-pages` branch.
  - `dvishoot.com` is set as the CNAME in the workflow.

### Production deploy flow (current)

1) Commit changes on `main`
2) Push to GitHub
3) GitHub Actions runs:
   - Checks out repo + submodules
   - Builds with `hugo --minify`
   - Deploys `public/` to `gh-pages`

You can check deploy status under **Actions** in your GitHub repo.

## Useful Files

- `hugo.yaml` — site config, menus, palette defaults
- `archetypes/posts.md` — default front matter for posts
- `archetypes/page.md` — default front matter for pages
- `assets/css/extended/custom.css` — all theme overrides
- `layouts/index.html` — custom home layout

---

If you want any additional editorial conventions (e.g., required front matter, series templates, or writing checklists), add them here so future you (or an LLM) can follow them consistently.
