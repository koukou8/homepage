# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

奥沢・自由が丘のパーソナルジム「STRETCH&STRENGTH」のホームページ。静的HTMLサイト。

## 環境

| 環境 | URL | ブランチ |
|------|-----|----------|
| 本番 | https://motorogu-essays-in-idleness.com/ | main |
| STG | https://koukou8.github.io/stretch-strength-homepage/ | main_stg |

## デプロイ

- **本番**: mainにマージ → GitHub Actions（`.github/workflows/deploy.yml`）でConoHa WingにFTPSデプロイ
- **STG**: main_stgにマージ → GitHub Pagesで自動公開

## 開発フロー

1. `main` からfeatureブランチを作成
2. feature → main へPR作成
3. PR作成時、GitHub Actionsが自動で main_stg にマージし、noindex有効化
4. STG環境で確認
5. mainにマージ → 本番デプロイ

## noindex制御

検索エンジンからの除外制御。HTMLファイルの`<head>`内に配置。

```html
<!-- 本番（コメントアウト状態） -->
<!--<meta name="robots" content="noindex" />-->

<!-- STG（有効化状態） -->
<meta name="robots" content="noindex" />
```

STGへの自動マージ時にGitHub Actionsがnoindexを有効化する。

## ファイル構成

- `index.html` - トップページ
- `service.html` - サービス紹介ページ
- `css/` - スタイルシート
- `images/` - 画像ファイル
- `icons/` - アイコンファイル
- `video/` - 動画ファイル

## CSSバージョニング

CSSファイルの読み込み時にクエリパラメータでバージョン管理：
```html
<link rel="stylesheet" type="text/css" href="css/index.css?v=20260107">
```
CSS変更時はバージョン番号（日付形式 YYYYMMDD）を更新してキャッシュ破棄。

## 構造化データ

index.htmlに`HealthClub`タイプのJSON-LD構造化データを実装済み。SEO対策として住所、営業時間、サービス情報を含む。

## ブラウザプレビュー確認

HTML/CSSファイルを変更した後は、Playwright MCPサーバーを使用してブラウザでプレビューを確認する。

### 確認手順

1. 変更したHTMLファイルをPlaywrightで開く
2. `browser_snapshot`でページ構造を確認
3. 必要に応じて`browser_take_screenshot`でスクリーンショットを撮影

### ローカルサーバー起動

Playwrightは`file://`プロトコルをサポートしないため、ローカルHTTPサーバーを使用する。

```bash
# プロジェクトディレクトリでサーバー起動（バックグラウンド）
python3 -m http.server 8080 &
```

### 確認対象URL

| ファイル | URL |
|----------|-----|
| トップページ | `http://localhost:8080/index.html` |
| サービスページ | `http://localhost:8080/service.html` |

### 使用例

```
# 1. ローカルサーバー起動（未起動の場合）
python3 -m http.server 8080 &

# 2. ページを開く
browser_navigate → http://localhost:8080/index.html

# 3. 表示確認
browser_snapshot → ページ構造の確認
browser_take_screenshot → 視覚的な確認
```
