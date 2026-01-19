# 変更をコミット

変更内容を確認し、適切なコミットメッセージを作成してコミットしてください。

## 手順

1. `git status` と `git diff` で変更内容を確認
2. `bin/rubocop` でスタイルチェック（エラーがあれば修正）
3. `bin/rails test` でテスト実行（失敗があれば報告）
4. 変更内容に基づいてコミットメッセージを作成
5. コミット実行

## コミットメッセージ規約

- 英語で記述
- 先頭は動詞: Add, Fix, Update, Remove, Refactor, Improve
- 50文字以内で簡潔に
- 必要に応じて本文で詳細説明

```
# フォーマット
<動詞> <変更内容の要約>

[任意: 詳細な説明]

# 例
Add streak bonus calculation to TrainingService
Fix geolocation check interval timing
Update user level-up logic for edge cases
Remove deprecated authentication method
Refactor gym proximity detection
```

## 追加指示

$ARGUMENTS

## 注意事項

- テストが失敗している場合はコミットせず、ユーザーに報告
- RuboCopエラーは `-a` オプションで自動修正を試みる
- 機密情報（.env、credentials等）が含まれていないか確認
- 大きな変更は論理的な単位で分割を提案
