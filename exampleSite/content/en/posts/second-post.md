---
title: "Using Tailwind CSS v4 with Hugo"
date: 2024-02-01
tags: [tailwind, css, hugo, frontend]
categories: [Tech]
description: "How the Flavor theme integrates Tailwind CSS v4 using Hugo's native asset pipeline, with no PostCSS required."
slug: tailwind-css-v4-hugo
cover:
  image: "https://picsum.photos/seed/tailwind-hugo/800/400"
---

## Why Tailwind CSS v4

Tailwind CSS v4 introduces a new engine built on Rust (Oxide), offering significantly faster build times compared to v3. For Hugo themes, this means near-instant CSS generation during development.

The key difference from v3 is the removal of the `tailwind.config.js` file. Configuration now lives directly in CSS using `@theme` directives:

```css
@import "tailwindcss";

@theme {
  --color-theme: #fafafa;
  --color-primary: #1a1a2e;
  --color-accent: #4f46e5;
  --color-border: #e5e7eb;
}
```

## Hugo Integration

Hugo 0.128+ includes native support for Tailwind CSS v4 via the `css.TailwindCSS` template function. No PostCSS configuration is needed. The build pipeline works as follows:

1. Hugo reads the main CSS file from `assets/css/`
2. The `css.TailwindCSS` pipe processes Tailwind directives
3. Output is minified in production builds

```go-html-template
{{ $css := resources.Get "css/main.css" }}
{{ $css = $css | css.TailwindCSS }}
{{ if hugo.IsProduction }}
  {{ $css = $css | minify | fingerprint }}
{{ end }}
<link rel="stylesheet" href="{{ $css.RelPermalink }}">
```

## Design Tokens

The Flavor theme defines design tokens as CSS custom properties. These tokens control the appearance across both light and dark modes:

| Token | Light Mode | Dark Mode |
|-------|-----------|-----------|
| `--color-theme` | `#fafafa` | `#1a1a2e` |
| `--color-primary` | `#1a1a2e` | `#e2e8f0` |
| `--color-accent` | `#4f46e5` | `#818cf8` |
| `--color-border` | `#e5e7eb` | `#2d2d44` |

To customize colors, override these properties in your own CSS file placed in `static/css/custom.css`:

```css
:root {
  --color-accent: #059669;
}
.dark {
  --color-accent: #34d399;
}
```

## Performance Considerations

Tailwind v4's Oxide engine compiles CSS in under 5ms for typical themes. Combined with Hugo's sub-second build times, the full site generation (including CSS) stays well under one second for most projects.
