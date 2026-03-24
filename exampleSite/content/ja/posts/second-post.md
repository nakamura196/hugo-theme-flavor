---
title: "HugoでTailwind CSS v4を使う方法"
date: 2024-02-01
tags: [tailwind, css, hugo, frontend]
categories: [Tech]
description: "FlavorテーマがHugoのネイティブアセットパイプラインを使ってTailwind CSS v4を統合する仕組みについて解説します。"
slug: tailwind-css-v4-hugo
cover:
  image: "https://picsum.photos/seed/tailwind-hugo/800/400"
---

## Tailwind CSS v4の特徴

Tailwind CSS v4はRustベースの新エンジン（Oxide）を採用しており、v3と比較してビルド時間が大幅に短縮されています。Hugoテーマにおいては、開発中のCSS生成がほぼ瞬時に行われます。

v3との主な違いは、`tailwind.config.js` が不要になった点です。設定はCSS内の `@theme` ディレクティブで直接記述します。

```css
@import "tailwindcss";

@theme {
  --color-theme: #fafafa;
  --color-primary: #1a1a2e;
  --color-accent: #4f46e5;
  --color-border: #e5e7eb;
}
```

## Hugoとの統合

Hugo 0.128以降では、`css.TailwindCSS` テンプレート関数によるTailwind CSS v4のネイティブサポートが含まれています。PostCSSの設定は不要です。ビルドパイプラインは以下のように動作します。

1. Hugoが `assets/css/` からメインCSSファイルを読み込む
2. `css.TailwindCSS` パイプがTailwindディレクティブを処理
3. 本番ビルドでは出力がミニファイされる

```go-html-template
{{ $css := resources.Get "css/main.css" }}
{{ $css = $css | css.TailwindCSS }}
{{ if hugo.IsProduction }}
  {{ $css = $css | minify | fingerprint }}
{{ end }}
<link rel="stylesheet" href="{{ $css.RelPermalink }}">
```

## デザイントークン

Flavorテーマはデザイントークンをcssカスタムプロパティとして定義しています。これらのトークンがライト・ダーク両モードの外観を制御します。

| トークン | ライトモード | ダークモード |
|----------|-------------|-------------|
| `--color-theme` | `#fafafa` | `#1a1a2e` |
| `--color-primary` | `#1a1a2e` | `#e2e8f0` |
| `--color-accent` | `#4f46e5` | `#818cf8` |
| `--color-border` | `#e5e7eb` | `#2d2d44` |

色をカスタマイズするには、`static/css/custom.css` に配置した独自のCSSファイルでこれらのプロパティを上書きします。

```css
:root {
  --color-accent: #059669;
}
.dark {
  --color-accent: #34d399;
}
```

## パフォーマンス

Tailwind v4のOxideエンジンは、一般的なテーマで5ms未満でCSSをコンパイルします。Hugoの1秒未満のビルド時間と組み合わせると、CSS生成を含むサイト全体の生成時間はほとんどのプロジェクトで1秒以内に収まります。
