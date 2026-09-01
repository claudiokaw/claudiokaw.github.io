# claudiokaw.github.io

Personal website / portfolio built with **Jekyll** and the **Minimal Mistakes**
theme (loaded via `remote_theme`, so it builds natively on GitHub Pages — no
GitHub Actions or local build required).

## Structure

```
_config.yml            Site + theme + author settings
_data/navigation.yml   Top navigation menu
index.md               About / home page
_pages/                Static pages: projects, articles, tutorials, competitions, cv
_posts/                Blog entries (articles & tutorials, split by `categories`)
_projects/             Projects collection (one file per project)
assets/images/         Images (avatar.jpg lives here)
assets/files/          Put your CV PDF here
```

Articles vs. tutorials are separated by the post's `categories` field:
`categories: [articles]` or `categories: [tutorials]`.

## Publish to GitHub Pages

1. Create a **public** repo on GitHub named exactly **`claudiokaw.github.io`**
   (empty — no README/license).
2. From this folder:

   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/claudiokaw/claudiokaw.github.io.git
   git push -u origin main
   ```

3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a
   branch**, branch **`main`**, folder **`/ (root)`**. Save.
4. Wait ~1–2 minutes. Your site goes live at **https://claudiokaw.github.io**.

## Before (or right after) you publish — fill in the placeholders

- **LinkedIn & Kaggle URLs** — edit `_config.yml` (search for `YOUR-LINKEDIN`
  and `YOUR-KAGGLE`).
- **Avatar** — `assets/images/avatar.jpg` is a temporary "CA" monogram. Replace
  it with a square photo (same filename), ~500×500px.
- **About text** — `index.md` is drafted from your background; paste your exact
  LinkedIn "About" text if you prefer.
- **CV PDF (optional)** — drop `cv.pdf` into `assets/files/` and uncomment the
  download line noted at the top of `_pages/cv.md`.

## Add new content

**New article:** create `_posts/YYYY-MM-DD-my-title.md`:

```markdown
---
title: "My article title"
date: 2026-09-15
categories: [articles]
tags: [payments, algorithms]
excerpt: "One-sentence summary."
---

Body in Markdown...
```

**New tutorial:** same as above but `categories: [tutorials]`.

**New project:** create `_projects/my-project.md`:

```markdown
---
title: "My project"
excerpt: "Short description shown on the Projects page."
date: 2026-09-15
tags: [Research, Optimization]
---

Body in Markdown...
```

## Preview locally (optional)

Requires Ruby. The included `Gemfile` uses the `github-pages` gem to match
GitHub's build exactly:

```bash
bundle install
bundle exec jekyll serve
# open http://localhost:4000
```

## Change the look

- Theme skin: `minimal_mistakes_skin` in `_config.yml`
  (`default`, `air`, `dark`, `contrast`, `sunrise`, `neon`, `mint`, `plum`, ...).
- Full theme docs: https://mmistakes.github.io/minimal-mistakes/docs/
