# ファイル構成計画ルール

## 目的

作業特性分析の結果をもとに、生成すべきルールファイルの一覧・各ファイルの役割・
ディレクトリ構造を設計し、コンストラクションフェーズの実行計画を立てる。

---

## 標準ファイル構成

すべての新しいワークフローは以下の標準構成を基本とする：

```
aidlc-rules/[作業名]/
├── core-workflow.md                    ← 必須
├── inception/
│   ├── context-detection.md            ← 必須
│   ├── requirements-analysis.md        ← 必須
│   ├── [作業固有のインセプションルール] ← 1〜3ファイル
│   └── workflow-planning.md            ← 複雑な作業のみ
├── construction/
│   ├── structure-design.md             ← 必須
│   ├── [作業固有のコンストラクションルール] ← 1〜3ファイル
│   └── review.md                       ← 必須
└── operations/
    └── [作業固有のオペレーションルール]  ← 後工程がある場合のみ

aidlc-docs/[作業名]/
└── aidlc-state.md                      ← 必須
```

---

## 作業固有ファイルの設計

作業特性分析の結果から、以下の観点で作業固有ファイルを決定する：

### インセプション固有ファイルの候補

| ファイル名のパターン | 作成する条件 |
|--------------------|------------|
| `audience-analysis.md` | 成果物の受け取り手・読み手の分析が重要な場合 |
| `[対象]-analysis.md` | 作業開始前に分析が必要な特定の対象がある場合 |
| `[作業名]-planning.md` | 実行前に構成や計画の設計が必要な場合 |
| `constraints-analysis.md` | 制約・前提条件の整理が作業品質に影響する場合 |

### コンストラクション固有ファイルの候補

| ファイル名のパターン | 作成する条件 |
|--------------------|------------|
| `draft-generation.md` | テキスト成果物を生成する場合 |
| `evaluation.md` | 対象を評価・採点・判定する場合 |
| `analysis-report.md` | 分析結果を構造化して出力する場合 |
| `action-plan.md` | 実行計画・タスクリストを生成する場合 |
| `template-filling.md` | 定型フォーマットを埋める作業の場合 |

### オペレーション固有ファイルの候補

| ファイル名のパターン | 作成する条件 |
|--------------------|------------|
| `submission-advice.md` | 成果物を誰かに提出・共有する場合 |
| `scheduling-advice.md` | 実施タイミングが重要な場合 |
| `followup-guide.md` | 成果物適用後のフォローアップが必要な場合 |
| `iteration-guide.md` | 定期的に繰り返す作業でサイクル管理が必要な場合 |

---

## 構成計画テンプレート

```markdown
## ファイル構成計画

### ディレクトリ名
`aidlc-rules/[作業名]/`

### 生成するファイルの一覧

#### 必須ファイル（常に生成）
- [ ] `core-workflow.md` — フェーズ定義・適応的実行ロジック
- [ ] `inception/context-detection.md` — [検出次元の内容]
- [ ] `inception/requirements-analysis.md` — [収集する情報]
- [ ] `construction/structure-design.md` — [成果物の構造]
- [ ] `construction/review.md` — [品質チェック項目]
- [ ] `aidlc-docs/[作業名]/aidlc-state.md` — セッション状態管理

#### 作業固有ファイル
- [ ] `inception/[ファイル名].md` — [役割]
- [ ] `construction/[ファイル名].md` — [役割]
- [ ] `operations/[ファイル名].md` — [役割]（後工程がある場合）

### 生成順序
1. core-workflow.md（全体像を先に確定する）
2. inception/ 配下のファイル（情報収集の設計）
3. construction/ 配下のファイル（成果物生成の設計）
4. operations/ 配下のファイル（後工程の設計）
5. aidlc-state.md（上記をもとに状態管理の項目を設計）

### CLAUDE.md への追記内容
`- **[作業の表示名]** — \`aidlc-rules/[作業名]/core-workflow.md\``
```

---

## 出力

ファイル構成計画はコンストラクションフェーズへの実行計画として引き渡す。
ユーザーに計画を提示し、承認を得てからファイル生成を開始する。

提示形式：
```
以下のファイル構成でワークフローを作成します。

[ファイル構成計画]

この構成でよろしいですか？問題なければ生成を開始します。
```
