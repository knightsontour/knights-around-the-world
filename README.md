# Knights on Tour

Travel blogs by Steve & Nicole Knight, published with [Hugo](https://gohugo.io) and the
[Beautiful Hugo](https://github.com/halogenica/beautifulhugo) theme, hosted on Cloudflare Pages.

## Structure

This is a **multi-blog** site. Each trip is its own section under `content/`, so new trips
can be added without disturbing existing ones.

```
content/
└── travel/
    └── knights-around-the-world-2017-18/   ← Trip 1 (live): 34 chapters
        ├── _index.md                        ← the trip's contents/landing page
        └── *.md                             ← one file per chapter
```

Coming next: `content/travel/big-lap-2024/` (the "Big Lap 2024" / *Knight Riders on Tour* epub).

## How content maps

Each chapter is a Markdown file with front matter:

```yaml
---
title: "05: Here we go!"      # leading number drives order
date: 2017-11-21
weight: 5                     # chapters sort by weight ascending (chronological)
tags: [travel, usa]
image: "/assets/imageN.jpg"   # thumbnail on listing pages
bigimg: [{src: "/assets/imageN.jpg", desc: ""}]   # hero banner on the post
---
```

- **Ordering**: `weight` (from the chapter number) → chapters list 01 → 34, oldest first.
- **Covers**: `image` + `bigimg` are set to each chapter's first photo.
- **Per-trip contents**: each trip's `_index.md` page (e.g. `/travel/knights-around-the-world-2017-18/`)
  lists all that trip's chapters in order.

## Local development

```bash
hugo server            # http://localhost:1313
hugo --gc --minify     # production build into ./public
```

The theme is a git submodule. After a fresh clone:

```bash
git submodule update --init --recursive
```

## Deploying

See [CLOUDFLARE-SETUP.md](CLOUDFLARE-SETUP.md). Once connected, `git push` to `main` auto-deploys.
