## リンク
### stg環境
https://koukou8.github.io/homepage/

### prod環境
https://motorogu-essays-in-idleness.com/

## タスク管理
- jira

## stg環境の運用
- Github Pagesで管理
- main_devブランチと紐付け
- 検索にヒットさせないため、main_devブランチにマージする際は全ページの<head>タグに下記を記述
```
<meta name="robots" content="noindex" />
```