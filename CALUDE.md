# CLAUDE.md

## .steering ディレクトリ（AIエージェント向けルールセット）

<!-- ### 技術文書ルール構成（`technical-writing-rule-details/` 配下）

| `writing-style.md` | 文体統一・冗長性排除 |
| `decision-documents.md` | 意思決定文書固有ルール |
| `review-checklist.md` | 提出前最終チェックリスト | -->

### 利用ガイドライン

- ソフトウェア開発タスクでは `aws-aidlc-rules/core-workflow.md` を最初に参照する
- 各フェーズ実行時は `aws-aidlc-rule-details/` 配下の該当ルールファイルを読み込む
- 共通ルール（`common/`）はワークフロー開始時に必ず読み込む
<!-- - サービス企画・設計が必要な場合は `service-design-rule-details/core-workflow.md` を先に実行する -->
<!-- - 技術文書作成時は `technical-writing-rule-details/introduction.md` から参照する -->
- セキュリティルールは全フェーズで必須の横断的制約として適用する（未充足はブロッキング）
<!-- - メール作成は下書きのみ。対象に応じた宛先ルールあり -->
