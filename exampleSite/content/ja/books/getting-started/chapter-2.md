---
title: "テーマのカスタマイズ"
bookSlug: "getting-started"
date: 2024-01-11
---

## カラースキーム

Flavorテーマはカラースキームにcssカスタムプロパティを使用しています。`static/css/custom.css` を作成して上書きできます。

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

テーマは `custom.css` が存在すれば自動的に読み込むため、テンプレートの変更は不要です。

## レイアウトの上書き

Hugoはテンプレートの検索順序を使用します。テーマのテンプレートを上書きするには、プロジェクトの `layouts/` ディレクトリに同じパスのファイルを作成します。

| テーマファイル | 上書き先 |
|--------------|----------|
| `themes/hugo-theme-flavor/layouts/_default/single.html` | `layouts/_default/single.html` |
| `themes/hugo-theme-flavor/layouts/partials/header.html` | `layouts/partials/header.html` |

例えば、全ページにカスタムバナーを追加するには `layouts/partials/extend_head.html` を作成します。

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

## ロゴの追加

ナビゲーションでテキストの代わりにロゴを使用するには、`hugo.yaml` を更新します。

```yaml
params:
  label:
    text: "My Site"
    icon: "/images/logo.png"
    iconHeight: 35
```

ロゴ画像は `static/images/logo.png` に配置します。

## 検索の設定

テーマは全文検索にPagefindを使用します。`hugo --minify` でサイトをビルドした後、Pagefindを実行して検索インデックスを生成します。

```bash
npx pagefind --site public
```

検索はすべての言語で機能します。検索ページは `/en/search/` と `/ja/search/` でそれぞれ利用できます。
