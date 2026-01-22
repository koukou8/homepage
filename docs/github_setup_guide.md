# GitHub管理セットアップガイド

## 前提条件
- GitHubアカウントが作成済みであること
- Gitがローカルマシンにインストール済みであること

## 手順

### 1. ローカルリポジトリの準備（完了済み）
```bash
cd /Users/koukiyoshida/stretch_strength/homepage
git init
```

### 2. GitHubでリポジトリを作成
1. GitHub（https://github.com）にログイン
2. 右上の「+」ボタンをクリック → 「New repository」を選択
3. 以下の設定を行う：
   - Repository name: `homepage` または任意の名前
   - Description: `Stretch & Strength gym homepage`（任意）
   - Public/Private: お好みで選択
   - **「Add a README file」「Add .gitignore」「Choose a license」はチェックしない**（既にローカルにファイルがあるため）
4. 「Create repository」をクリック

### 3. ローカルリポジトリとGitHubリポジトリの連携
GitHubでリポジトリを作成後、表示されるコマンドの2番目のセクション「…or push an existing repository from the command line」を使用します。

```bash
# リモートリポジトリを追加（YOUR_USERNAMEを実際のGitHubユーザー名に変更）
git remote add origin https://github.com/YOUR_USERNAME/homepage.git

# デフォルトブランチをmainに変更（推奨）
git branch -M main
```

### 4. 初回コミットとプッシュ
```bash
# 全ファイルをステージング
git add .

# 初回コミット
git commit -m "Initial commit: Add homepage files"

# GitHubにプッシュ
git push -u origin main
```

## 今後の運用

### ファイルを更新した場合
```bash
# 変更をステージング
git add .

# コミット（メッセージは変更内容に合わせて記述）
git commit -m "Update: 変更内容の説明"

# GitHubにプッシュ
git push
```

### よく使うGitコマンド
```bash
# 現在の状況確認
git status

# 変更履歴確認
git log --oneline

# 特定のファイルのみステージング
git add ファイル名

# 直前のコミットメッセージを修正
git commit --amend -m "新しいメッセージ"
```

## 注意事項
- `.DS_Store`ファイルは`.gitignore`で除外済み
- 大きなファイル（動画ファイルなど）は注意が必要（GitHubの制限は100MB）
- プライベートリポジトリの場合は、アクセス権限に注意
- 定期的にバックアップとしてプッシュすることを推奨

## GitHub Pages（ウェブサイト公開）
もしウェブサイトを無料で公開したい場合：
1. リポジトリの「Settings」タブ
2. 左サイドバーの「Pages」
3. Source を「Deploy from a branch」に設定
4. Branch を「main」、folder を「/ (root)」に設定
5. 「Save」をクリック

数分後、`https://YOUR_USERNAME.github.io/homepage/` でサイトが公開されます。 