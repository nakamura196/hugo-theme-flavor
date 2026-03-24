---
title: "インストールとセットアップ"
bookSlug: "getting-started"
date: 2024-01-10
---

## 前提条件

Flavorテーマをインストールする前に、以下のツールがシステムにインストールされていることを確認します。

- **Hugo extended edition**（v0.128以降）— Tailwind CSS v4のサポートに必要
- **Git** — テーマをサブモジュールとして管理するため
- **Node.js**（v18以上）— 開発時のTailwind CSS CLIに必要

Hugoのインストールを確認するには以下を実行します。

```bash
hugo version
# hugo v0.139.0+extended darwin/arm64
```

## 新しいサイトの作成

新しいHugoプロジェクトを作成し、Flavorテーマを追加します。

```bash
hugo new site my-blog
cd my-blog
git init
git submodule add https://github.com/yourname/hugo-theme-flavor themes/hugo-theme-flavor
```

次に、サンプル設定をコピーします。

```bash
cp themes/hugo-theme-flavor/exampleSite/hugo.yaml .
```

## ディレクトリ構成

セットアップ後のプロジェクト構成は以下のようになります。

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

`content/` ディレクトリは言語ごとに整理されています。各言語はそれぞれのサブディレクトリを持ち、バイリンガルコンテンツには同じスラッグを使用します。

## 開発サーバーの起動

ローカル開発サーバーを起動します。

```bash
hugo server -D
```

`-D` フラグは下書き記事を含めます。`http://localhost:1313/ja/` にアクセスしてサイトを確認します。Hugoはファイルの変更を監視し、ブラウザを自動的にリロードします。
