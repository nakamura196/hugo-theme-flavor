# Flavor

[![Hugo](https://img.shields.io/badge/Hugo-%3E%3D0.157-ff4088?logo=hugo)](https://gohugo.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/nakamura196/hugo-theme-flavor?style=social)](https://github.com/nakamura196/hugo-theme-flavor)

A modern Hugo theme built with Tailwind CSS v4. Clean design with dark/light mode, multilingual support (45+ languages), sticky sidebar TOC, full-text search, and a books content type.

![Screenshot](images/screenshot.png)

---

## Table of Contents

- [Features](#features)
- [Demo](#demo)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Content](#content)
- [Customization](#customization)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [Credits](#credits)
- [License](#license)

## Features

- **Tailwind CSS v4** -- Built with Hugo's native `css.TailwindCSS` pipeline, no PostCSS needed
- **Dark / Light Mode** -- Auto-detection via `prefers-color-scheme` with manual toggle and smooth transitions
- **Multilingual (i18n)** -- 45+ built-in translations with language switcher in header
- **Sticky Sidebar TOC** -- Table of contents with active heading highlight on scroll
- **Full-Text Search** -- Pagefind integration with sort by relevance, newest, or oldest
- **Books Content Type** -- Structured book/chapter layout with sidebar navigation and prev/next links
- **Archives** -- Chronological post listing grouped by year and month
- **Categories & Tags** -- Taxonomy pages with card-style category listing
- **SEO** -- OpenGraph, Twitter Cards, JSON-LD schema markup, canonical URLs
- **Share Buttons** -- X/Twitter, LinkedIn, Reddit, Facebook, WhatsApp, Telegram, Hacker News
- **Code Copy Buttons** -- One-click copy on all code blocks
- **Related Articles** -- Automatically shown at the end of posts
- **Reading Time & Word Count** -- Configurable post metadata display
- **Buy Me a Coffee** -- Built-in support button (language-aware)
- **Edit Post Link** -- Link to source file on GitHub/GitLab
- **Cover Images** -- Per-post thumbnail images on list and single pages
- **Hero Section** -- Homepage hero with site stats (articles, books, tags) and popular tags
- **Breadcrumbs** -- Configurable breadcrumb navigation
- **Scroll to Top** -- Floating button with smooth scroll
- **Responsive** -- Mobile-first with hamburger menu and collapsible sidebars
- **Accessibility** -- Skip-to-content link, ARIA labels, focus styles, semantic HTML
- **Custom Fonts** -- Google Fonts integration via config
- **Video Shortcode** -- Embed local MP4 videos
- **RSS Feed** -- Built-in RSS output
- **Pagination** -- Configurable page size with optional page numbers
- **Comments** -- Extensible comment system via `comments.html` partial
- **Syntax Highlighting** -- Chroma-based with dark/light mode support

## Demo

Live demo: **<https://nakamura196.pages.dev/>**

## Requirements

- [Hugo](https://gohugo.io/) **0.157.0** or later (extended edition)
- [Node.js](https://nodejs.org/) 18+ (for Tailwind CSS CLI and Pagefind)
- [Go](https://go.dev/) 1.21+ (only if using Hugo Modules installation method)

## Installation

### Method 1: Hugo Modules (recommended)

Initialize Hugo Modules in your project:

```bash
hugo mod init github.com/your-username/your-site
```

Add the theme to your `hugo.yaml`:

```yaml
module:
  imports:
    - path: github.com/nakamura196/hugo-theme-flavor
```

Install Node.js dependencies:

```bash
npm install -D tailwindcss @tailwindcss/cli @tailwindcss/typography pagefind
```

### Method 2: Git Submodule

```bash
git submodule add https://github.com/nakamura196/hugo-theme-flavor.git themes/hugo-theme-flavor
```

Set the theme in `hugo.yaml`:

```yaml
theme: "hugo-theme-flavor"
```

Install Node.js dependencies:

```bash
npm install -D tailwindcss @tailwindcss/cli @tailwindcss/typography pagefind
```

### Run the Dev Server

Tailwind CLI must be on your `PATH`:

```bash
PATH=$PWD/node_modules/.bin:$PATH hugo server
```

### Build for Production

```bash
PATH=$PWD/node_modules/.bin:$PATH hugo --minify && npx pagefind --site public
```

## Configuration

Below is a full `hugo.yaml` example showing all available parameters.

```yaml
baseURL: "https://example.com/"
title: "My Blog"
theme: "hugo-theme-flavor"

pagination:
  pagerSize: 10

defaultContentLanguage: en
defaultContentLanguageInSubdir: true

languages:
  en:
    languageName: "English"
    weight: 1
    contentDir: "content/en"
    title: "My Tech Blog"
    params:
      description: "A blog about technology and development"
      homeInfoParams:
        Title: "My Tech Blog"
        Subtitle: "Optional subtitle above the title"
        Content: "Welcome to my blog about technology"
    menu:
      main:
        - name: Home
          url: /en/
          weight: 1
        - name: Articles
          url: /en/posts/
          weight: 2
        - name: Books
          url: /en/books/
          weight: 3
        - name: Archives
          url: /en/archives/
          weight: 4
        - name: Categories
          url: /en/categories/
          weight: 5
        - name: Search
          url: /en/search/
          weight: 6
        - name: About
          url: /en/about/
          weight: 7
      footer:
        - name: Articles
          url: /en/posts/
          weight: 1
          params:
            group: Content
        - name: Tags
          url: /en/tags/
          weight: 2
          params:
            group: Browse
        - name: About
          url: /en/about/
          weight: 3
          params:
            group: Other

params:
  env: production
  author: "Your Name"
  description: "Site-wide description for SEO"
  keywords: [blog, tech]
  defaultTheme: auto          # light | dark | auto
  mainSections: ["posts"]
  DateFormat: ":date_long"

  # Header
  label:
    text: "My Blog"           # header logo text (defaults to site title)

  # Homepage hero
  homeInfoParams:
    Title: "Welcome"
    Subtitle: "Optional small text above title"
    Content: "A short tagline for the hero section"

  # Post display
  showReadingTime: true
  showWordCount: false
  showToc: true
  showBreadCrumbs: true
  showCodeCopyButtons: true
  showPostNavLinks: true
  ShowShareButtons: true      # share icons on posts
  ShowPageNums: false          # page numbers in pagination
  ShowAllPagesInArchive: true  # include all sections in archives
  disableAnchoredHeadings: false

  # UI toggles
  disableThemeToggle: false
  disableLangToggle: false
  disableScrollToTop: false

  # Buy Me a Coffee
  buyMeACoffeeUsername: "your-username"

  # Edit post link
  editPost:
    URL: "https://github.com/your-username/your-repo/edit/main/content"
    Text: "Suggest changes"
    appendFilePath: true

  # Social (used in Twitter Cards)
  social:
    twitter: "your_handle"

  # Custom fonts
  fonts:
    google_fonts_url: "https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;600;700&display=swap"
    sans: '"Noto Sans JP", sans-serif'
    serif: '"Noto Serif JP", serif'
    mono: '"Fira Code", monospace'

  # Favicons
  assets:
    favicon: "favicon.ico"
    favicon16x16: "favicon-16x16.png"
    favicon32x32: "favicon-32x32.png"
    apple_touch_icon: "apple-touch-icon.png"

taxonomies:
  category: categories
  tag: tags

outputs:
  home:
    - HTML
    - RSS

markup:
  goldmark:
    renderer:
      unsafe: true
  tableOfContents:
    startLevel: 2
    endLevel: 3
  highlight:
    noClasses: false
```

### Site Parameters Reference

| Parameter | Type | Default | Description |
|---|---|---|---|
| `defaultTheme` | string | `auto` | `light`, `dark`, or `auto` |
| `mainSections` | list | `["posts"]` | Sections shown on the home page |
| `label.text` | string | site title | Header logo text |
| `homeInfoParams.Title` | string | -- | Hero section title |
| `homeInfoParams.Subtitle` | string | -- | Small text above hero title |
| `homeInfoParams.Content` | string | -- | Hero section subtitle/tagline |
| `showReadingTime` | bool | `false` | Show estimated reading time |
| `showWordCount` | bool | `false` | Show word count in post meta |
| `showToc` | bool | `false` | Show sticky sidebar table of contents |
| `showBreadCrumbs` | bool | `false` | Show breadcrumb navigation |
| `showCodeCopyButtons` | bool | `false` | Show copy button on code blocks |
| `showPostNavLinks` | bool | `false` | Show prev/next post links |
| `ShowShareButtons` | bool | `false` | Show social share buttons on posts |
| `ShowPageNums` | bool | `false` | Show page numbers in pagination |
| `ShowAllPagesInArchive` | bool | `false` | Include all sections in archive page |
| `buyMeACoffeeUsername` | string | -- | Buy Me a Coffee username |
| `disableThemeToggle` | bool | `false` | Hide dark/light toggle button |
| `disableLangToggle` | bool | `false` | Hide language switcher |
| `disableScrollToTop` | bool | `false` | Hide scroll-to-top button |
| `DateFormat` | string | `:date_long` | Go time format for dates |
| `author` | string | -- | Default author name |
| `editPost.URL` | string | -- | Base URL for "edit this post" link |
| `editPost.Text` | string | `Edit` | Edit link display text |
| `editPost.appendFilePath` | bool | `false` | Append file path to edit URL |

### Menus

The theme uses two menus: `main` (header navigation) and `footer`.

Footer menu items support a `group` parameter for column grouping:

```yaml
menu:
  footer:
    - name: About
      url: /about/
      params:
        group: Other
```

## Content

### Posts

Place posts in `content/{lang}/posts/`. Full frontmatter reference:

```yaml
---
title: "Article Title"
date: '2024-01-15T10:00:00+09:00'
lastmod: '2024-02-01T00:00:00+09:00'  # optional, shown when different from date
draft: false
tags: [hugo, tailwind]
categories: [Tech]
slug: my-article-slug
description: "Brief description shown in meta and post header"
author: "Author Name"                  # overrides site-level author
keywords: [keyword1, keyword2]         # overrides tags for meta keywords
canonicalURL: "https://example.com/original"  # custom canonical URL
source: "https://example.com/original" # source/origin URL link

cover:
  image: "/images/articles/my-image.png"
  hidden: false                        # hide cover on both list and single
  hiddenInSingle: false                # hide cover only on single page
  relative: false                      # true if image path is relative to page bundle

# Per-post overrides
hideMeta: false            # hide the date/author/reading-time line
hideAuthor: false          # hide author only
hideSummary: false         # hide summary on list pages
hideFooter: false          # hide the site footer
hiddenInHomeList: false    # exclude from homepage listing
disableShare: false        # hide share buttons for this post
disableAnchoredHeadings: false
robotsNoIndex: false       # add noindex meta tag
comments: false            # enable comments section
editPost:
  URL: ""                  # per-post edit URL override
  disabled: false
---
```

### Books

The books content type provides structured, multi-chapter content with sidebar navigation.

Directory structure:

```text
content/en/books/
  _index.md              # books listing page
  my-book/
    _index.md            # book overview (with chapters list)
    chapter-1.md         # individual chapter
    chapter-2.md
```

Book `_index.md` frontmatter:

```yaml
---
title: "My Book Title"
description: "Book description"
bookSlug: my-book
cover:
  image: "/images/books/my-book-cover.png"
tags: [topic1, topic2]
source: "https://example.com/original"
chapters:
  - title: "Chapter 1: Getting Started"
    slug: chapter-1
  - title: "Chapter 2: Deep Dive"
    slug: chapter-2
---
```

Chapter frontmatter:

```yaml
---
title: "Chapter 1: Getting Started"
bookSlug: my-book
---
```

### Special Pages

**Search page** -- create `content/{lang}/search.md`:

```yaml
---
title: "Search"
layout: "search"
---
```

**Archives page** -- create `content/{lang}/archives.md`:

```yaml
---
title: "Archives"
layout: "archives"
---
```

**About page** -- create `content/{lang}/about.md`:

```yaml
---
title: "About"
---
Your content here.
```

### Video Shortcode

Embed local videos in posts:

```text
{{</* video src="/videos/demo.mp4" width="720" */>}}
```

## Customization

### Colors

Override CSS custom properties by creating your own stylesheet (loaded via `extend_head.html`). The theme defines these variables for both light and dark modes:

| Variable | Light | Dark | Description |
|---|---|---|---|
| `--color-theme` | `#fafafa` | `#0f172a` | Page background |
| `--color-entry` | `#ffffff` | `#1e293b` | Card/entry background |
| `--color-primary` | `#1a1a2e` | `#e2e8f0` | Primary text |
| `--color-secondary` | `#6b7280` | `#94a3b8` | Secondary text |
| `--color-tertiary` | `#f3f4f6` | `#1e293b` | Tertiary background |
| `--color-border` | `#e5e7eb` | `#334155` | Border color |
| `--color-accent` | `#4f46e5` | `#818cf8` | Accent / links |
| `--color-accent-light` | `#818cf8` | `#a5b4fc` | Accent hover |
| `--color-code-bg` | `#f1f5f9` | `#334155` | Inline code background |
| `--color-code-block-bg` | `#1e1e2e` | `#0f172a` | Code block background |

### Fonts

Override default fonts (Inter) via `params.fonts` in your `hugo.yaml`:

```yaml
params:
  fonts:
    google_fonts_url: "https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;600;700&display=swap"
    sans: '"Noto Sans JP", sans-serif'
    serif: '"Noto Serif JP", serif'
    mono: '"Fira Code", monospace'
```

The theme maps these to `--font-sans`, `--font-serif`, and `--font-mono` CSS custom properties.

### Extending Templates

The theme provides two empty partials for injecting custom code:

- **`layouts/partials/extend_head.html`** -- Injected at the end of `<head>`. Use for custom CSS, analytics scripts, or meta tags.
- **`layouts/partials/extend_footer.html`** -- Injected before the closing `</body>`. Use for custom JS, chat widgets, etc.

Create these files in your project's `layouts/partials/` directory to override the theme defaults.

### Comments

The theme renders `layouts/partials/comments.html` on posts where `comments: true` is set in frontmatter. Override this partial in your project to integrate any comment system (Disqus, Giscus, Utterances, etc.).

## Deployment

### Cloudflare Pages

Build command:

```bash
PATH=$PWD/node_modules/.bin:$PATH hugo --minify && npx pagefind --site public
```

Build output directory: `public`

Environment variable: `HUGO_VERSION` = `0.157.0` (or later)

### Netlify

`netlify.toml`:

```toml
[build]
  command = "PATH=$PWD/node_modules/.bin:$PATH hugo --minify && npx pagefind --site public"
  publish = "public"

[build.environment]
  HUGO_VERSION = "0.157.0"
  NODE_VERSION = "18"
```

### GitHub Pages

Use a GitHub Actions workflow that installs Hugo (extended), Node.js, runs the build command above, and deploys the `public` directory.

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Credits

- [Hugo](https://gohugo.io/) -- Static site generator
- [Tailwind CSS](https://tailwindcss.com/) -- Utility-first CSS framework
- [Pagefind](https://pagefind.app/) -- Static full-text search

## License

[MIT License](LICENSE)
