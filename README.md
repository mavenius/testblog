# Aveni Blog

A minimal Jekyll blog (default `minima` theme) built and deployed to Cloudflare Pages via GitHub Actions.

Source repo: `github.com/mavenius/testblog`. Published at `https://testblog.pages.dev/` (exact subdomain confirmed on first successful deploy).

## Structure

- `_config.yml` — site config (title, theme, plugins)
- `_posts/` — blog posts, one file per post, named `YYYY-MM-DD-title.md`
- `index.md` — home page (lists posts via the `home` layout)
- `.github/workflows/cloudflare-pages.yml` — builds the site with Jekyll and deploys it to Cloudflare Pages on every push to `main`

## Publishing this repo to Cloudflare Pages (one-time setup)

1. Create (or use an existing) Cloudflare account.
2. Create an API token at **dash.cloudflare.com/profile/api-tokens** with `Account > Cloudflare Pages > Edit` permission.
3. Find the **Account ID** in the Cloudflare dashboard sidebar.
4. In the GitHub repo, go to **Settings → Secrets and variables → Actions** and add:
   - `CLOUDFLARE_API_TOKEN` — the token from step 2
   - `CLOUDFLARE_ACCOUNT_ID` — the ID from step 3
5. Push to `main` (or run the `Deploy Jekyll site to Cloudflare Pages` workflow from the Actions tab). The workflow builds the site and deploys it, creating the Cloudflare Pages project (`testblog`) on first run.
6. The site becomes reachable at `https://testblog.pages.dev/` (or a custom domain added later via the Cloudflare Pages dashboard).

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
