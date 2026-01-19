# PRを作成

現在のブランチの変更内容を確認し、Pull Requestを作成してください。

## 手順

1. 現在のブランチと変更内容を確認
   - `git branch --show-current`
   - `git log main..HEAD --oneline`
   - `git diff main...HEAD --stat`

2. CI チェックを実行
   - `bin/rubocop`
   - `bin/rails test`

3. リモートにプッシュ（未プッシュの場合）
   - `git push -u origin <branch-name>`

4. `gh pr create` でPRを作成

## PRテンプレート

```markdown
## 概要
<!-- 変更の目的と背景を1-2文で -->

## 変更内容
<!-- 主な変更点を箇条書きで -->
-

## テスト
<!-- テスト方法や確認事項 -->
- [ ] `bin/rails test` 通過
- [ ] `bin/rubocop` 通過
- [ ] 動作確認済み

## スクリーンショット
<!-- UI変更がある場合 -->

## 関連Issue
<!-- 関連するIssue番号があれば -->
```

## 追加指示

$ARGUMENTS

## 注意事項

- `main` ブランチからは直接PRを作成しない
- コミットが整理されているか確認（必要に応じてsquash提案）
- CIチェックが失敗している場合は修正を優先
- ドラフトPRにする場合は `--draft` オプションを使用
