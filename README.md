## リンク
### stg環境
https://koukou8.github.io/stretch-strength-homepage/

### prod環境
https://motorogu-essays-in-idleness.com/

## タスク管理
- jira

## stg環境の運用
- Github Pagesで管理
- main_stgブランチと紐付け
- 検索にヒットさせないため、main_devブランチにマージする際は全ページの<head>タグに下記を記述
```
<meta name="robots" content="noindex" />
```

## 改修時の開発手順
1. mainから作業ブランチfeature/を切って修正
2. feature/ → mainのPR作成
3. ローカルfeature/でnoindexを追加
4. feature/ → main_stgのPR作成
5. main_stgマージ
6. Github Pages確認
7. 問題なければローカルfeature/でnoindexを削除
8. mainにpush
9. mainマージ
10. サーバーにアップロード
