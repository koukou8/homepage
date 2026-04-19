## リンク
### stg環境
https://koukou8.github.io/stretch-strength-homepage/

### prod環境
https://motorogu-essays-in-idleness.com/

## タスク管理
- jira

## デプロイ

- **本番**: mainにマージ → GitHub Actions（`.github/workflows/deploy.yml`）でConoHa WingにFTPSデプロイ
- **STG**: main_stgにマージ → GitHub Pages（https://koukou8.github.io/stretch-strength-homepage/）で自動公開

## GitHub Actions ワークフロー詳細

### `auto-merge-to-stg.yml` — STG自動マージ

**トリガー**: `main` へのPRが作成（opened）またはコミット追加（synchronize）されたとき。

**処理の流れ:**
1. featureブランチを `main_stg` にマージ
2. `index.html` / `service.html` の noindex タグを `sed` でコメントアウト解除
   ```
   <!--<meta name="robots" content="noindex" />-->  →  <meta name="robots" content="noindex" />
   ```
3. 変更をコミットして `main_stg` にpush → GitHub Pagesに自動反映

> PRにコミットを追加するたびに再実行されるため、STGは常に最新状態になる。

### `deploy.yml` — 本番デプロイ

**トリガー**: `main` ブランチへのpush（＝PRマージ）。

**処理**: FTPS経由でConoHa Wingの `/public_html/motorogu-essays-in-idleness.com/` へファイル転送。  
`.git/`・`.md`・`.DS_Store` などは除外。noindexはコメントアウトされたままデプロイされる。

---

## 改修時の開発手順
1. mainから作業ブランチfeature/を切って修正
2. feature/ → main へPR作成
3. PR作成時にGitHub Actionsが自動でmain_stgへマージ（noindexも自動で有効化）
4. STG環境で確認
5. 問題なければmainにマージ → 本番デプロイ
