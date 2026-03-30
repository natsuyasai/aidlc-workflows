# ワークフロー定義ファイル作成 コアワークフロー

## 概要

このワークフロー自体が AI-DLC の方法論で動作するメタワークフローです。
「特定の業務・作業を AI-DLC で支援するためのワークフロー定義ファイル一式」を
新たに作成することを目的とします。

作成されるファイル群は、このリポジトリの `business-email` や `tech-blog` と
同じ構造に準拠し、将来の Claude Code セッションで即座に利用できる状態になります。

---

## フェーズ1：インセプション — 対象作業の本質を把握する

**目的：** 新しいワークフローの対象となる作業を深く理解し、
必要なフェーズ・ステージ・ルールファイルの設計方針を決定する。

### ステージ1.1 — コンテキスト検出（常に実行）

ユーザーが提供した情報を評価する：

- **情報が十分**：作業の名称・目的・自然なライフサイクルがすべて判明 → ステージ1.3へ
- **情報が一部不足**：ステージ1.2（要件分析）を実行
- **情報がほぼない**：インセプション全体（ステージ1.2〜1.4）を実行

ルールを読み込む：`aidlc-rules/workflow-creator/inception/context-detection.md`

### ステージ1.2 — 要件分析（情報が不足している場合に実行）

対象作業の特性を明確にするための質問を行う。
一度に質問するのは最大5問まで。

ルールを読み込む：`aidlc-rules/workflow-creator/inception/requirements-analysis.md`

### ステージ1.3 — 作業特性分析（常に実行）

対象作業の自然なライフサイクル・繰り返し構造・品質基準を分析し、
AI-DLC の3フェーズ（インセプション・コンストラクション・オペレーション）への
マッピングを決定する。

ルールを読み込む：`aidlc-rules/workflow-creator/inception/task-analysis.md`

### ステージ1.4 — ファイル構成計画（常に実行）

生成すべきルールファイルの一覧・各ファイルの役割・ディレクトリ構造を設計する。

ルールを読み込む：`aidlc-rules/workflow-creator/inception/workflow-planning.md`

---

## フェーズ2：コンストラクション — ワークフロー定義ファイルを生成する

**目的：** 設計したファイル構成に従い、すべてのルールファイルを生成する。

### ステージ2.1 — コアワークフロー生成（常に実行）

対象作業の `core-workflow.md` を生成する。
フェーズ定義・各ステージの実行条件・適応的実行の原則を含む。

ルールを読み込む：`aidlc-rules/workflow-creator/construction/core-workflow-template.md`

### ステージ2.2 — インセプションルール生成（常に実行）

`context-detection.md` / `requirements-analysis.md` および
作業固有のインセプションルールファイルを生成する。

ルールを読み込む：`aidlc-rules/workflow-creator/construction/inception-rules-template.md`

### ステージ2.3 — コンストラクションルール生成（常に実行）

`structure-design.md` / `draft-generation.md` / `review.md` に相当する
作業固有のコンストラクションルールファイルを生成する。

ルールを読み込む：`aidlc-rules/workflow-creator/construction/construction-rules-template.md`

### ステージ2.4 — オペレーションルール生成（作業に後工程がある場合に実行）

スキップ条件：作業が成果物の完成で終わる（配布・公開・適用などの後工程がない）場合。
実行条件：完成した成果物を誰かに届ける・適用するなどの後工程がある場合。

ルールを読み込む：`aidlc-rules/workflow-creator/construction/operations-rules-template.md`

### ステージ2.5 — セッション状態ファイル生成（常に実行）

`aidlc-state.md` テンプレートを生成する。

ルールを読み込む：`aidlc-rules/workflow-creator/construction/state-template.md`

### ステージ2.6 — 全体レビュー（常に実行）

生成したファイル群を横断的にレビューし、一貫性・網羅性・実用性を確認する。

ルールを読み込む：`aidlc-rules/workflow-creator/construction/review.md`

---

## フェーズ3：オペレーション — 生成したワークフローを統合・運用する

**目的：** 生成したワークフローをリポジトリに組み込み、
実際に使える状態にするためのアドバイスを提供する。

### ステージ3.1 — 統合アドバイス（ユーザーが求めた場合に実行）

CLAUDE.md への追記方法・ディレクトリ配置・動作確認の手順を提供する。

ルールを読み込む：`aidlc-rules/workflow-creator/operations/integration-advice.md`

---

## 適応的実行の原則

| 条件 | アクション |
|------|-----------|
| 作業名と目的が明確に伝わっている | ステージ1.2をスキップし1.3から開始 |
| 「アウトラインだけ先に確認したい」 | 1.4（ファイル構成計画）のみ実行し承認を得てから生成へ |
| 既存ワークフローに近い作業 | 最も類似したワークフローを参照元として明示し差分のみ設計 |
| 後工程（配布・適用など）がない作業 | ステージ2.4をスキップ |
| ユーザーが特定ファイルの修正を求めた | 該当ステージのみ再実行 |

## 成果物の保存

生成したすべてのファイルを `aidlc-docs/workflow-creator/generated/[作業名]/` に保存する。
実際のルールファイルは `aidlc-rules/[作業名]/` に配置する。
セッション状態を `aidlc-docs/workflow-creator/aidlc-state.md` で管理する。
