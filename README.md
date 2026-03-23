# Flavor - A Modern Hugo Theme

A clean, modern Hugo theme built with Tailwind CSS v4. Features dark/light mode, multilingual support, sticky sidebar TOC, and responsive design.

![Screenshot](images/screenshot.png)

## Features

- **Tailwind CSS v4** — Built with Hugo's native `css.TailwindCSS` pipeline
- **Dark/Light Mode** — Auto-detection with manual toggle, smooth transitions
- **Multilingual** — Full i18n support with language switcher
- **Sticky Sidebar TOC** — Table of contents with active heading highlight
- **Responsive** — Mobile-first with hamburger menu
- **Search** — Pagefind integration for fast full-text search
- **Books** — Structured book/chapter content type with sidebar navigation
- **Archives** — Chronological post listing grouped by year/month
- **SEO** — OpenGraph, Twitter Cards, JSON-LD schema markup
- **Accessibility** — Focus styles, ARIA labels, semantic HTML

## Requirements

- Hugo **0.157.0** or later (extended edition)
- Node.js 18+ (for Tailwind CSS CLI and Pagefind)

## Quick Start

### 1. Add the theme

```bash
git submodule add https://github.com/nakamura196/hugo-theme-flavor.git themes/hugo-theme-flavor
```

### 2. Install dependencies

```bash
npm install -D tailwindcss @tailwindcss/cli @tailwindcss/typography pagefind
```

### 3. Configure

In `hugo.yaml`:

```yaml
theme: "hugo-theme-flavor"

params:
  defaultTheme: auto
  mainSections: ["posts"]
  showReadingTime: true
  showToc: true
  showBreadCrumbs: true
  showCodeCopyButtons: true
  label:
    text: "My Blog"
  homeInfoParams:
    Title: "Welcome"
    Content: "A blog about technology"
```

### 4. Run

```bash
PATH=$PWD/node_modules/.bin:$PATH hugo server
```

## Configuration

### Site Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `defaultTheme` | string | `auto` | `light`, `dark`, or `auto` |
| `mainSections` | list | `["posts"]` | Sections to show on home page |
| `label.text` | string | site title | Header logo text |
| `homeInfoParams.Title` | string | — | Hero section title |
| `homeInfoParams.Content` | string | — | Hero section subtitle |
| `showReadingTime` | bool | `false` | Show reading time in post meta |
| `showToc` | bool | `false` | Show table of contents sidebar |
| `showBreadCrumbs` | bool | `false` | Show breadcrumb navigation |
| `showCodeCopyButtons` | bool | `false` | Show copy button on code blocks |
| `showPostNavLinks` | bool | `false` | Show prev/next post links |
| `buyMeACoffeeUsername` | string | — | Buy Me a Coffee username |
| `disableThemeToggle` | bool | `false` | Hide dark/light toggle |
| `disableLangToggle` | bool | `false` | Hide language switcher |
| `disableScrollToTop` | bool | `false` | Hide scroll-to-top button |

### Custom Fonts

Override default fonts via `params.fonts`:

```yaml
params:
  fonts:
    google_fonts_url: "https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;600;700&display=swap"
    sans: '"Noto Sans JP", sans-serif'
    serif: '"Noto Serif JP", serif'
```

### Menus

The theme uses two menus: `main` (header navigation) and `footer` (footer columns).

Footer menu items support a `group` parameter for column grouping:

```yaml
menu:
  footer:
    - name: About
      url: /about/
      params:
        group: Other
```

### Search

Search is powered by [Pagefind](https://pagefind.app/). After building with Hugo, run Pagefind to generate the search index:

```bash
hugo --minify && npx pagefind --site public
```

Create a search page in your content:

```markdown
---
title: "Search"
layout: "search"
---
```

### Books

The theme supports structured book content with chapters. See the [Books documentation](docs/books.md) for details.

## Content Types

### Posts

Standard blog posts in `content/{lang}/posts/`.

### Books

Structured content with chapters in `content/{lang}/books/`.

### Archives

Add an archives page:

```markdown
---
title: "Archives"
layout: "archives"
---
```

## Development

```bash
cd exampleSite
npm install
npm run dev
```

## Credits

- [Tailwind CSS](https://tailwindcss.com/) — Utility-first CSS framework
- [Pagefind](https://pagefind.app/) — Static search library
- [Hugo](https://gohugo.io/) — Static site generator

## License

MIT License. See [LICENSE](LICENSE) for details.
