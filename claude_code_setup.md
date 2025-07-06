# Claude Code活用セットアップガイド

## ディレクトリ構造の拡張

```
talent-ecosystem-project/
├── README.md
├── prompts/                     # 既存のプロンプトテンプレート
├── outputs/                     # 新規：各段階の出力を保存
│   └── [人物名]/               # 人物ごとのディレクトリ
│       ├── stage1a_mapping.md   # Stage 1Aの出力
│       ├── stage1b_research.md  # Stage 1Bの出力
│       ├── stage2_analysis.md   # Stage 2の出力
│       ├── stage3_structure.md  # Stage 3の出力
│       ├── final_article.md     # 最終記事
│       └── references.md        # 参考文献リスト
├── scripts/                     # 新規：自動化スクリプト
│   ├── run_stage1a.sh          # Stage 1A実行スクリプト
│   ├── run_stage1b.sh          # Stage 1B実行スクリプト
│   ├── run_stage2.sh           # Stage 2実行スクリプト
│   ├── run_stage3.sh           # Stage 3実行スクリプト
│   ├── run_stage4.sh           # Stage 4実行スクリプト
│   └── run_all_stages.sh       # 全段階実行スクリプト
└── templates/                   # 既存のテンプレート

```

## 実行方法（Claude Codeの制限を考慮）

### ⚠️ 重要：Claude Codeには検索機能がありません
- **Stage 1A/1B（調査）**：通常のClaude（Web検索機能あり）で実行
- **Stage 2-4（分析・執筆）**：Claude Codeで実行（ファイル操作中心）

### Stage 1A: 才能家系図作成【通常のClaude使用】
```
1. 通常のClaudeチャットで以下を実行：
「対象人物：宇多田ヒカル
C:\ClaudeWork\talent-ecosystem-project\prompts\stage1a_mapping.mdの内容に従って、
Web検索を使用して才能家系図を作成してください。」

2. 結果をコピーして、手動でファイルに保存：
C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage1a_mapping.md

※または、Claudeに「結果をMarkdown形式でダウンロード可能にしてください」と依頼
```

### Stage 1B: 戦略的深掘り調査【通常のClaude使用】
```
1. 通常のClaudeチャットで以下を実行：
「前段階の成果物：[Stage 1Aの内容をペースト]
C:\ClaudeWork\talent-ecosystem-project\prompts\stage1b_deep_dive.mdに従って、
リサーチ機能で深掘り調査を実施してください。」

2. 結果をファイルに保存：
C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage1b_research.md
```

### Stage 2: 関係性分析【Claude Code使用開始】
```bash
# ここからClaude Codeが効果的！
claude-code "
前段階の成果物を読み込み：
- C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage1a_mapping.md
- C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage1b_research.md

C:\ClaudeWork\talent-ecosystem-project\prompts\stage2_analysis.mdのプロンプトを使用して、
才能の関係性を分析してください。

結果は以下のファイルに保存：
C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage2_analysis.md
"
```

### Stage 3: 記事構成
```bash
claude-code "
前段階の成果物を読み込み：
- C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage2_analysis.md

C:\ClaudeWork\talent-ecosystem-project\prompts\stage3_structure.mdのプロンプトを使用して、
記事構成を作成してください。

結果は以下のファイルに保存：
C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage3_structure.md
"
```

### Stage 4: 執筆
```bash
claude-code "
前段階の成果物を読み込み：
- C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage3_structure.md
- C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\stage2_analysis.md

C:\ClaudeWork\talent-ecosystem-project\prompts\stage4_writing.mdのプロンプトを使用して、
最終記事を執筆してください。

結果は以下のファイルに保存：
C:\ClaudeWork\talent-ecosystem-project\outputs\utada_hikaru\final_article.md
"
```

## 使い分けのメリット

### 1. 最適なツールを最適な場面で使用
- **調査段階（Stage 1A/1B）**：通常ClaudeのWeb検索機能をフル活用
- **分析・執筆段階（Stage 2-4）**：Claude Codeでファイル操作と長時間作業

### 2. チャット容量の効率的な活用
- 調査で容量を使い切っても、分析はClaude Codeで新規開始
- 各段階で最適なコンテキストサイズを維持

### 2. 性能の向上
- コンテキストが小さく保たれるため、応答が高速かつ正確
- 各段階に集中できるため、品質が向上
- エラーが発生しても該当段階だけやり直せる

### 3. 成果物の管理
- すべての中間成果物が保存される
- 後から見直しや修正が容易
- 複数の人物について並行して作業可能

### 4. 再利用性
- プロンプトテンプレートを他の人物にも適用可能
- 成功パターンを蓄積して改善
- チーム作業も可能に

## 実行時の注意点

1. **ディレクトリの作成**
   - 各人物の出力ディレクトリを事前に作成
   - `mkdir -p outputs/[人物名]`

2. **段階的実行**
   - 必ず順番通りに実行（1A→1B→2→3→4）
   - 前段階の出力を確認してから次へ

3. **品質チェック**
   - 各段階の出力を確認
   - 必要に応じて再実行や修正

4. **時間管理**
   - Stage 1A: 30-45分
   - Stage 1B: 1-1.5時間
   - Stage 2: 30-45分
   - Stage 3: 30分
   - Stage 4: 45-60分
   - 合計: 約4-5時間（休憩含む）

## 発展的な活用

### 1. バッチ処理
複数の人物を連続処理するスクリプトの作成

### 2. テンプレートのカスタマイズ
特定の分野（音楽、文学、科学など）に特化したプロンプト

### 3. 分析ツールの開発
- 才能関係性の可視化ツール
- パターン分析の自動化
- 法則抽出の支援ツール

### 4. コラボレーション
- GitHubでのバージョン管理
- チームでの分担作業
- レビュープロセスの確立

このセットアップにより、Claude Codeを最大限活用して、
効率的かつ高品質な才能生態学の記事を作成できます。