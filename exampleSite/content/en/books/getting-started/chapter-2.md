---
title: "Customizing Your Theme"
bookSlug: "getting-started"
date: 2024-01-11
---

## Color Scheme

The Flavor theme uses CSS custom properties for its color scheme. You can override them by creating `static/css/custom.css`:

```css
:root {
  --color-accent: #059669;
  --color-accent-hover: #047857;
}

.dark {
  --color-accent: #34d399;
  --color-accent-hover: #6ee7b7;
}
```

The theme automatically loads `custom.css` if it exists, so no template changes are needed.

## Layout Overrides

Hugo uses a lookup order for templates. To override any theme template, create a file with the same path in your project's `layouts/` directory:

| Theme File | Override Location |
|-----------|-------------------|
| `themes/hugo-theme-flavor/layouts/_default/single.html` | `layouts/_default/single.html` |
| `themes/hugo-theme-flavor/layouts/partials/header.html` | `layouts/partials/header.html` |

For example, to add a custom banner to every page, create `layouts/partials/extend_head.html`:

```go-html-template
<style>
  .custom-banner {
    background: var(--color-accent);
    color: white;
    padding: 0.5rem 1rem;
    text-align: center;
  }
</style>
```

## Adding a Logo

To use a logo instead of text in the navigation, update `hugo.yaml`:

```yaml
params:
  label:
    text: "My Site"
    icon: "/images/logo.png"
    iconHeight: 35
```

Place the logo image in `static/images/logo.png`.

## Search Configuration

The theme uses Pagefind for full-text search. After building your site with `hugo --minify`, run Pagefind to generate the search index:

```bash
npx pagefind --site public
```

Search works across all languages. The search page is available at `/en/search/` and `/ja/search/` respectively.
