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

## テーマの変更

### 1. 新しいテーマを探す

Hugo公式テーマサイトでテーマを探します：https://themes.gohugo.io/

### 2. 現在のテーマを削除

```bash
# サブモジュールを削除
git submodule deinit themes/ananke
git rm themes/ananke
rm -rf .git/modules/themes/ananke
```

### 3. 新しいテーマを追加

```bash
# 例：PaperModテーマを追加する場合
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

### 4. 設定ファイルを更新

`hugo.toml` でテーマ名を変更：

```toml
theme = 'PaperMod'  # 新しいテーマ名に変更
```

### 5. テーマ固有の設定を追加

各テーマの README を参照して、必要な設定を `hugo.toml` に追加します。

### 6. ローカルで確認

```bash
hugo server --buildDrafts
```

### 7. 変更をデプロイ

```bash
git add .
git commit -m "テーマを変更: 新テーマ名"
git push origin main
```

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
