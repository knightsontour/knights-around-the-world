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
---
```

- **Ordering**: `weight` (from the chapter number) → chapters list 01 → 34, oldest first.
- **Covers**: `image` (listing thumbnail) is set to each chapter's first photo.
- **No hero banners**: do NOT add the `bigimg` hero-banner field. Steve's standing rule —
  banner images are never published unless he explicitly asks for them on a given post.
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

## Adding a new trip

1. Add the trip's content under `content/travel/<trip-slug>/` (an `_index.md` with
   `title` + `subtitle`, plus one `.md` per chapter).
2. It **auto-appears as a tile** on the homepage (tiles are generated from the trip
   sections; the thumbnail is the trip's first chapter photo, or set `image` on the trip's
   `_index.md` to choose one).
3. Add it to the **Trips dropdown** by appending one block to `hugo.toml`:

   ```toml
   [[menu.main]]
     parent = "trips"
     name = "Big Lap 2024"
     url = "/travel/big-lap-2024/"
     weight = 2
   ```

## Deploying

See [CLOUDFLARE-SETUP.md](CLOUDFLARE-SETUP.md). Once connected, `git push` to `main` auto-deploys.
