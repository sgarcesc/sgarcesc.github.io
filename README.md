# sebastiangarces.com

Personal site of Sebastian Garces, built with [Jekyll](https://jekyllrb.com/) 4 and deployed to
GitHub Pages by a GitHub Actions workflow.

## Structure

| Path | Purpose |
|---|---|
| `index.html` | Landing page (hero, about, latest writing) |
| `_config.yml` | Site metadata, author details and landing-page links |
| `_layouts/` | `default` (page shell) and `post` layouts |
| `_includes/icon.html` | Inline SVG icons used by the links |
| `_posts/` | Blog posts, named `YYYY-MM-DD-title.md` |
| `assets/` | Stylesheet and favicon |
| `.github/workflows/pages.yml` | Builds on every PR; builds and deploys on push to `main` |

## Writing a post

Create `_posts/2026-01-31-my-post.md`:

```markdown
---
layout: post
title: My post
---

Hello, Middle-earth.
```

It appears in the **Writing** section on the landing page and in `/feed.xml`.

## Running locally

Requires Ruby 3.x and Bundler.

```sh
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>.

## Deployment

Pushing to `main` runs `.github/workflows/pages.yml`, which builds the site with
`JEKYLL_ENV=production` and publishes it with `actions/deploy-pages`. The repository's
**Settings → Pages → Source** must be set to **GitHub Actions**.

The custom domain (`sebastiangarces.com`) is configured in the repository's Pages settings and
served through Cloudflare, which handles HTTPS.
