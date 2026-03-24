---
title: "HugoとFlavorテーマの導入ガイド"
date: 2024-01-15
tags: [hugo, theme, static-site]
categories: [Tech]
description: "Hugoの静的サイトジェネレーターにFlavorテーマを導入する手順と、主要な設定項目について紹介します。"
slug: hello-world
cover:
  image: "https://picsum.photos/seed/hugo-flavor/800/400"
---

## インストール

HugoはGo言語で書かれた高速な静的サイトジェネレーターです。Flavorテーマを使うには、Hugo extended editionをインストールして新しいサイトを作成します。

```bash
hugo new site mysite
cd mysite
git init
git submodule add https://github.com/yourname/hugo-theme-flavor themes/hugo-theme-flavor
```

クローン後、`exampleSite/hugo.yaml` をプロジェクトルートにコピーします。テーマはTailwind CSS v4を使用しており、Hugoの組み込み `css.TailwindCSS` パイプが自動的に処理します。

## 設定の概要

テーマの設定は `hugo.yaml` で管理します。主な設定項目は以下の通りです。

- **`defaultContentLanguage`** — メインの言語を指定（例: `en`）
- **`params.showToc`** — サイドバーの目次を有効化
- **`params.defaultTheme`** — `auto`、`light`、`dark` から選択
- **`params.showReadingTime`** — 記事の推定読了時間を表示

最小限の設定例:

```yaml
baseURL: "https://example.com/"
theme: "hugo-theme-flavor"
defaultContentLanguage: en

params:
  showToc: true
  defaultTheme: auto
  showReadingTime: true
```

## テーマの機能

Flavorテーマには以下の機能が含まれています。

| 機能 | 説明 |
|------|------|
| ダーク/ライトモード | システム設定に基づく自動切り替え |
| 多言語対応 | `en`、`ja` など複数言語をサポート |
| Pagefind検索 | 多言語対応の全文検索 |
| 固定TOC | スクロールに追従するサイドバー目次 |
| Tailwind CSS v4 | HugoパイプによるユーティリティファーストCSS |

> テーマはCSSカスタムプロパティを使用しているため、ダーク・ライトモード間で色が自動的に切り替わります。

## 記事の作成

Hugoのコンテンツジェネレーターを使って新しい記事を作成します。

```bash
hugo new content/ja/posts/my-first-post.md
```

各記事のフロントマターでは `title`、`date`、`tags`、`categories`、`description`、`cover.image` などのフィールドを指定できます。`slug` フィールドでURLパスを制御します。
