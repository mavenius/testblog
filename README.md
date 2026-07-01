# Aveni Blog

A minimal Jekyll blog (default `minima` theme) built for GitHub Pages via GitHub Actions.

Confirmed destination: `github.com/mavenius/testblog`, published at `https://mavenius.github.io/testblog/`.

## Structure

- `_config.yml` — site config (title, theme, plugins)
- `_posts/` — blog posts, one file per post, named `YYYY-MM-DD-title.md`
- `index.md` — home page (lists posts via the `home` layout)
- `.github/workflows/pages.yml` — builds the site with Jekyll and deploys it to GitHub Pages on every push to `main`

## Publishing this repo to GitHub Pages (one-time setup)

1. Create a new empty GitHub repository at `github.com/mavenius/testblog`, then push this directory's contents to its `main` branch:
   ```
   git remote add origin https://github.com/mavenius/testblog.git
   git push -u origin main
   ```
   (This directory is already a git repo with the scaffold committed on `main`.)
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, select **GitHub Actions** (not "Deploy from a branch").
4. Push to `main` (or re-run the `Deploy Jekyll site to Pages` workflow from the Actions tab). The workflow builds the site and deploys it.
5. The site becomes reachable at `https://<org-or-user>.github.io/<repo-name>/` (or at the repo's custom domain, if one is configured via a `CNAME` file and DNS).

## Adding a new post

Add a file to `_posts/` named `YYYY-MM-DD-title.md`:

```markdown
---
layout: post
title: "My New Post"
date: 2026-07-01 12:00:00 +0000
---

Post content in Markdown.
```

Push to `main` and the Actions workflow republishes the site automatically.

## Custom domain (optional)

To use a custom domain instead of the default `github.io` URL, add a `CNAME` file at the repo root containing the domain, and point the domain's DNS at GitHub Pages per [GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
