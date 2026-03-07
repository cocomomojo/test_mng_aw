---
name: pr-test-generator
description: Generate test cases and issue from PR metadata + diff
engine: copilot
on:
   workflow_run:
     workflows: ["make issue and test case from pr diff"]
     types:
       - completed
permissions:
  contents: read
  actions: read
safe-outputs:
   create-issue: ~
---

# PR テストケース生成
目的:
PR のタイトル・本文・差分から、実行可能なテスト項目を Markdown チェックリストとして生成する。

手順:
1. PR メタ情報（タイトル、本文、作成者、ラベル）を確認する。
2. `git diff`（変更ファイル/変更箇所）から影響範囲（コンポーネント、ページ、API）を特定する。
3. 以下の観点でテストを抽出する（該当するもののみ）:
   - 機能
   - 回帰
   - 境界値
   - セキュリティ
   - パフォーマンス
   - UI
4. 各テスト項目は次の要素で記述する:
   - **タイトル**（1行）
   - **説明**（1文）
   - **期待結果**（1文）
   - 必要時のみ **手順**（最大3ステップ）
5. 出力の先頭に短い要約を付ける:
   - 影響コンポーネント
   - 信頼度（高/中/低）
6. 差分がドキュメント/コメントのみなら、短い注記のみ出力し、テスト項目は作成しない。
7. 生成する Issue はドラフト相当の内容で作成し、ラベル `ai-generated-tests` を付与する。

出力形式:
- Markdown チェックリスト
- 例:
  - [ ] **ログイン: 無効なパスワード** — 間違ったパスワードでログインを試行する; *期待:* 「認証に失敗しました」と表示される。
  - [ ] **プロフィール: アバターアップロード** — 大きな画像をアップロードする; *期待:* 画像が受け入れられリサイズされる。

制約:
- 秘密情報やソースコード全文は出力しない。
- 各テスト項目は簡潔に（最大2行）。
- 不確実な点は「要レビュー」など保守的に記載する。