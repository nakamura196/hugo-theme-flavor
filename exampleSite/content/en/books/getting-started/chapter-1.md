---
title: "Installation and Setup"
bookSlug: "getting-started"
date: 2024-01-10
---

## Prerequisites

Before installing the Flavor theme, make sure you have the following tools available on your system:

- **Hugo extended edition** (v0.128 or later) — required for Tailwind CSS v4 support
- **Git** — for managing the theme as a submodule
- **Node.js** (v18+) — needed for the Tailwind CSS CLI during development

You can verify your Hugo installation with:

```bash
hugo version
# hugo v0.139.0+extended darwin/arm64
```

## Creating a New Site

Start by creating a new Hugo project and adding the Flavor theme:

```bash
hugo new site my-blog
cd my-blog
git init
git submodule add https://github.com/yourname/hugo-theme-flavor themes/hugo-theme-flavor
```

Then copy the example configuration:

```bash
cp themes/hugo-theme-flavor/exampleSite/hugo.yaml .
```

## Directory Structure

After setup, your project should look like this:

```text
my-blog/
├── content/
│   ├── en/
│   │   └── posts/
│   └── ja/
│       └── posts/
├── hugo.yaml
├── static/
└── themes/
    └── hugo-theme-flavor/
```

The `content/` directory is organized by language. Each language has its own subdirectory with matching slugs for bilingual content.

## Running the Development Server

Start the local development server:

```bash
hugo server -D
```

The `-D` flag includes draft posts. Open `http://localhost:1313/en/` to see your site. Hugo watches for file changes and reloads the browser automatically.
