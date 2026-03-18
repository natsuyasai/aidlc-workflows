# CLAUDE.md

## .steering ディレクトリ（AIエージェント向けルールセット）

## 有効なワークフロー

- ソフトウェア開発タスク — `aidlc-rules/sdd/core-workflow.md`
- **ビジネスメール作成** — `aidlc-rules/business-email/core-workflow.md`
- **技術ブログ執筆** — `aidlc-rules/tech-blog/core-workflow.md`
- **ワークフロー定義ファイル作成** — `aidlc-rules/workflow-creator/core-workflow.md`


### 利用ガイドライン

- 各フェーズ実行時は `aws-aidlc-rule-details/` 配下の該当ルールファイルを読み込む
- 共通ルール（`aidlc-rules/common/`）はワークフロー開始時に必ず読み込む
- セキュリティルールは全フェーズで必須の横断的制約として適用する（未充足はブロッキング）

セッション中に生成したすべての成果物は `aidlc-docs/` に保存します。

## ドキュメント構成

```
aidlc-docs/
├── business-email/
│   ├── aidlc-state.md       # 現在のセッション状態
│   ├── audit.md             # セッション監査ログ
│   └── drafts/              # 生成したメールドラフト
├── tech-blog/
│   ├── aidlc-state.md       # 現在のセッション状態
│   ├── audit.md             # セッション監査ログ
│   └── drafts/              # 生成したブログ記事ドラフト
├── workflow-creator/
│   ├── aidlc-state.md       # 現在のセッション状態
│   ├── audit.md             # セッション監査ログ
│   └── generated/           # 生成したワークフロー定義ファイル一式
```

