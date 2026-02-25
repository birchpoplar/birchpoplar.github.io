# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Hugo static site blog deployed to GitHub Pages at `https://birchpoplar.github.io/`. It uses the [hugo-bearblog](https://github.com/janraasch/hugo-bearblog) theme as a Git submodule.

## Common Commands

```bash
# Serve locally with live reload
hugo server

# Serve including draft posts
hugo server -D

# Build for production (output to ./public)
hugo --minify

# Create a new blog post
hugo new blog/<post-name>/index.md
```

## Deployment

Pushing to `master` triggers the GitHub Actions workflow (`.github/workflows/hugo.yml`), which builds and deploys the site to GitHub Pages automatically. The `public/` directory is the build output — do not manually commit generated files there.

## Content Structure

- `content/_index.md` — Homepage
- `content/blog/_index.md` — Blog listing page
- `content/blog/<post-slug>/index.md` — Individual blog posts (page bundles)
- Place post-specific images inside the post's directory (e.g. `content/blog/<post-slug>/image.png`)

### Front Matter Format

Posts use TOML front matter (delimited by `+++`):

```toml
+++
title = "Post Title"
author = ["Johnnie"]
date = 2026-02-20
draft = false
+++
```

Set `draft = true` to keep a post unpublished until ready.

## Theme

The active theme is `hugo-bearblog` (Git submodule at `themes/hugo-bearblog`). Configuration lives in `hugo.toml`. Key settings:

- `permalinks.blog = "/:slug/"` — Bearblog-style clean URLs
- `disableKinds = ["taxonomy"]` — Taxonomies disabled intentionally
- `markup.goldmark.renderer.unsafe = true` — Allows raw HTML in Markdown
- `enablePostNavigator = true` — Previous/next post navigation enabled

The `themes/ritzy` submodule is present but not active.
