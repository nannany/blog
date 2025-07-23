# My Blog

Hugo製の静的サイトブログです。

## ローカル開発

### 前提条件

- Hugo（Extended版）がインストールされていること

```bash
# macOSの場合
brew install hugo
```

### 起動方法

1. リポジトリをクローン後、サブモジュールを初期化

```bash
git submodule update --init --recursive
```

2. 開発サーバーを起動

```bash
hugo server --buildDrafts
```

3. ブラウザで http://localhost:1313 にアクセス

### 記事の作成と公開

#### 1. 新しい記事を作成

```bash
hugo new content posts/記事名.md
```

#### 2. 記事を編集

作成されたMarkdownファイルを編集します。

```markdown
+++
date = '2025-07-23T22:41:07+09:00'
draft = false  # 公開する場合はfalseに変更
title = '記事のタイトル'
tags = ['タグ1', 'タグ2']
+++

# 記事の内容をMarkdownで記述

本文をここに書きます。
```

#### 3. ローカルで確認

```bash
hugo server --buildDrafts
```

#### 4. 記事を公開

```bash
# 変更をコミット
git add .
git commit -m "新しい記事を追加: 記事のタイトル"

# GitHubにプッシュ（自動デプロイが実行されます）
git push origin main
```

#### 5. 公開確認

数分後に https://nannany.github.io/blog/ で記事が公開されていることを確認

### ビルド

```bash
hugo
```

ビルド後のファイルは `public/` ディレクトリに出力されます。

## GitHub Pages デプロイ

このリポジトリは GitHub Actions を使用して自動的に GitHub Pages にデプロイされます。

### デプロイ手順

1. `main` ブランチにプッシュすると自動デプロイが実行されます

### 確認

デプロイ後、https://nannany.github.io/blog/ でサイトを確認できます。

### 注意事項

- `.github/workflows/hugo.yaml` でHugoのバージョンを指定しています
- サブモジュール（テーマ）も自動的に取得されます
- デプロイには数分かかる場合があります
