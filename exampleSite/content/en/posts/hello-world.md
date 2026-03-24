---
title: "Getting Started with Hugo and the Flavor Theme"
date: 2024-01-15
tags: [hugo, theme, static-site]
categories: [Tech]
description: "A walkthrough of setting up Hugo with the Flavor theme, covering installation, configuration, and key features."
slug: hello-world
cover:
  image: "https://picsum.photos/seed/hugo-flavor/800/400"
---

## Installation

Hugo is a fast static site generator written in Go. To get started with the Flavor theme, install Hugo extended edition and create a new site:

```bash
hugo new site mysite
cd mysite
git init
git submodule add https://github.com/yourname/hugo-theme-flavor themes/hugo-theme-flavor
```

After cloning, copy the example configuration from `exampleSite/hugo.yaml` to your project root. The theme requires Tailwind CSS v4, which Hugo's built-in `css.TailwindCSS` pipe handles automatically.

## Configuration Overview

The theme is configured through `hugo.yaml`. Key settings include:

- **`defaultContentLanguage`** — sets the primary language (e.g., `en`)
- **`params.showToc`** — enables the sticky sidebar table of contents
- **`params.defaultTheme`** — choose `auto`, `light`, or `dark`
- **`params.showReadingTime`** — displays estimated reading time on posts

A minimal configuration looks like this:

```yaml
baseURL: "https://example.com/"
theme: "hugo-theme-flavor"
defaultContentLanguage: en

params:
  showToc: true
  defaultTheme: auto
  showReadingTime: true
```

## Theme Features

The Flavor theme includes several features out of the box:

| Feature | Description |
|---------|-------------|
| Dark/Light Mode | Automatic toggle based on system preference |
| Multilingual | Built-in support for `en`, `ja`, and more |
| Pagefind Search | Full-text search with multi-language support |
| Sticky TOC | Sidebar table of contents that follows scroll |
| Tailwind CSS v4 | Modern utility-first CSS via Hugo pipes |

> The theme uses CSS custom properties for theming, so colors adapt seamlessly between dark and light modes.

## Creating Your First Post

Create a new post using Hugo's content generator:

```bash
hugo new content/en/posts/my-first-post.md
```

Each post supports frontmatter fields like `title`, `date`, `tags`, `categories`, `description`, and `cover.image`. The `slug` field controls the URL path.
