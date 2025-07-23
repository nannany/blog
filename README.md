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

### 記事の作成

```bash
hugo new content posts/記事名.md
```

### ビルド

```bash
hugo
```

ビルド後のファイルは `public/` ディレクトリに出力されます。
