# Caeruleum | 任我行 — Personal Blog

A personal blog built with [Hugo](https://gohugo.io/) and the [MemE](https://github.com/reuixiy/hugo-theme-meme/) theme, deployed on [Vercel](https://vercel.com/).

**Live site:** https://blog-yaoyiw27s-projects.vercel.app/

---

## Content

| Section | Path | Description |
|---------|------|-------------|
| Home | `content/home/` | Welcome page |
| Tech | `content/tech/` | Technical notes and learning logs |
| Work | `content/work/` | Co-op and work term reflections |

---

## Prerequisites

- [Hugo](https://gohugo.io/installation/) **v0.86.0 or later** (extended version recommended)
- Git

Check your Hugo version:

```bash
hugo version
```

---

## Local Development

**1. Clone the repo (including the theme submodule)**

```bash
git clone --recurse-submodules https://github.com/YaoyiW27/Blog.git
cd Blog
```

If you already cloned without `--recurse-submodules`, initialize the theme:

```bash
git submodule update --init --recursive
```

**2. Start the dev server**

```bash
hugo server -D
```

- `-D` includes draft posts
- Open http://localhost:1313 in your browser
- The server live-reloads on file changes

---

## Writing Posts

**Create a new post using an archetype:**

```bash
hugo new tech/my-post-title.md
hugo new work/my-work-log.md
```

This generates a file pre-filled with frontmatter:

```yaml
---
title: "My Post Title"
date: 2024-01-01T00:00:00+00:00
draft: true
---
```

Set `draft: false` (or remove the field) when the post is ready to publish.

**Useful frontmatter fields:**

```yaml
---
title: "Post Title"
date: 2024-01-01
draft: false
tags: ["hugo", "go"]
categories: ["tech"]
description: "A short summary shown in previews."
---
```

---

## Build

Generate the static site into the `public/` directory:

```bash
hugo --minify
```

The `public/` folder is git-ignored — Vercel builds it automatically on each push to `main`.

---

## Deployment

The site deploys automatically via **Vercel** whenever changes are pushed to the `main` branch. No manual steps required.

---

## Theme

This blog uses the [MemE](https://github.com/reuixiy/hugo-theme-meme/) theme. All site-wide configuration lives in `config.toml`. Key settings:

| Setting | Location in `config.toml` |
|---------|--------------------------|
| Site title & author | `[params]` → `siteName`, `author*` |
| Dark/light mode | `[params]` → `enableDarkMode` |
| Menu items | `[[menu.main]]` sections |
| Fonts & colors | `[params]` → `fontFamilyBody`, `primaryColorLight` |

---

## Project Structure

```
Blog/
├── archetypes/       # Templates for new content (hugo new ...)
├── content/          # Markdown posts organized by section
│   ├── home/
│   ├── tech/
│   └── work/
├── layouts/          # Custom HTML overrides and shortcodes
├── static/           # Static assets (images, fonts, audio)
├── themes/meme/      # MemE theme (git submodule)
├── public/           # Generated site output (git-ignored)
└── config.toml       # Hugo + theme configuration
```
