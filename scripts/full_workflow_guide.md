# 才能生態学プロジェクト - Claude Code実行ガイド（全段階）

## 事前準備

### 1. 出力ディレクトリの作成
```bash
# Windows (Command Prompt)
mkdir outputs
mkdir outputs\[人物名]

# 例：宇多田ヒカルの場合
mkdir outputs\utada_hikaru
```

### 2. プロジェクトディレクトリの確認
```
C:\ClaudeWork\talent-ecosystem-project\
├── prompts\          # プロンプトファイル（確認済み）
├── outputs\          # 出力ディレクトリ（新規作成）
└── scripts\          # 実行スクリプト（このファイル）
```

## 段階的実行コマンド（使い分け版）

### 🔍 Stage 1A: 才能家系図作成（30-45分）【通常のClaude使用】
```
通常のClaudeチャットで実行：
「[人物名]の才能家系図を作成します。
C:\ClaudeWork\talent-ecosystem-project\prompts\stage1a_mapping.mdの内容に従って、
Web検索で関係者を洗い出してください。
結果はダウンロード可能なMarkdown形式で出力してください。」

→ 結果をC:\ClaudeWork\talent-ecosystem-project\outputs\[人物名]\stage1a_mapping.mdに保存
```

### 🔍 Stage 1B: 戦略的深掘り調査（1-1.5時間）【通常のClaude使用】  
```
通常のClaudeチャットで実行：
「Stage 1Aの結果：[stage1a_mapping.mdの内容をペースト]

C:\ClaudeWork\talent-ecosystem-project\prompts\stage1b_deep_dive.mdに従って、
リサーチ機能で重要人物の深掘り調査を実施してください。」

→ 結果をC:\ClaudeWork\talent-ecosystem-project\outputs\[人物名]\stage1b_research.mdに保存
```

### 📊 Stage 2: 関係性分析（30-45分）【Claude Code使用開始】
```bash
# ここからClaude Codeが活躍！
claude-code "タスク：Stage 1A/1Bの結果を読み込み、関係性を分析。プロンプトファイル（C:\ClaudeWork\talent-ecosystem-project\prompts\stage2_analysis.md）を使用。多段階影響、循環構造、建設的挫折を分析し、結果はC:\ClaudeWork\talent-ecosystem-project\outputs\[人物名]\stage2_analysis.mdに保存。"
```

### 📝 Stage 3: 記事構成（30分）【Claude Code使用】
```bash
claude-code "タスク：Stage 2の分析結果を基に記事構成を作成。プロンプトファイル（C:\ClaudeWork\talent-ecosystem-project\prompts\stage3_structure.md）を使用。生態系の複雑度に応じた文字数設定と構成案を作成し、結果はC:\ClaudeWork\talent-ecosystem-project\outputs\[人物名]\stage3_structure.mdに保存。"
```

### ✍️ Stage 4: 執筆（45-60分）【Claude Code使用】
```bash
claude-code "タスク：Stage 3の構成に基づき最終記事を執筆。プロンプトファイル（C:\ClaudeWork\talent-ecosystem-project\prompts\stage4_writing.md）を使用。全段階の成果物を参照し、設定文字数で記事を完成させる。結果はC:\ClaudeWork\talent-ecosystem-project\outputs\[人物名]\final_article.mdに保存。"
```

## 使い分けのポイント

### 🎯 ツール選択の基準
| Stage | ツール | 理由 |
|-------|---------|------|
| 1A/1B | 通常Claude | Web検索・リサーチ機能が必須 |
| 2-4 | Claude Code | ファイル操作・長時間作業に最適 |

### 💾 ファイル保存のコツ
- **Stage 1A/1B後**：結果を確実にファイル保存
- **マークダウン形式**：コピー＆ペーストしやすい
- **ファイル名統一**：stage1a_mapping.md など

## 実行のコツ

### 1. 段階的な品質確認
- 各段階の出力を確認してから次へ進む
- 不十分な場合は該当段階を再実行

### 2. 時間管理
- Total: 約4-5時間
- 休憩を挟みながら実行
- 集中力が必要なStage 1B/4は体調の良い時に

### 3. エラー対処
- ファイルが見つからない：パスを確認
- 容量制限：該当段階だけを新しいチャットで実行
- 検索エラー：時間を置いて再実行

### 4. 成果物の活用
- 中間成果物も価値がある（研究資料として）
- 複数人物の比較分析に活用
- プロンプトの改善に反映

## カスタマイズ例

### 音楽家向け
```
claude-code "タスク：音楽家[人物名]の才能家系図作成。音楽的影響（作曲技法、演奏スタイル、プロデューサー等）に特に注目して調査。"
```

### 作家向け
```
claude-code "タスク：作家[人物名]の才能家系図作成。文学的影響（編集者、文学賞審査員、同人誌仲間等）に特に注目して調査。"
```

### 起業家向け
```
claude-code "タスク：起業家[人物名]の才能家系図作成。ビジネス的影響（メンター、投資家、共同創業者等）に特に注目して調査。"
```

## トラブルシューティング

### Q: チャット容量制限に達した
A: 
- **Stage 1A/1Bで制限**：結果を保存して、Stage 2からClaude Codeで再開
- **Stage 2-4で制限**：該当Stageを新しいClaude Codeタスクで実行

### Q: 検索結果が少ない
A: Stage 1Aを別の検索キーワードで再実行。日本語/英語両方で検索。

### Q: 文字数が多すぎる
A: Stage 3で前編・後編分割を検討。または重要度の低い要素を削減。

### Q: 関係性が複雑すぎる
A: Stage 2で主要関係者を絞り込み。補足記事として別途作成も検討。

## 成功のポイント

### 🔄 ハイブリッドアプローチの利点
1. **調査力の最大化**：通常Claudeの検索機能をフル活用
2. **作業効率の最適化**：Claude Codeのファイル操作で高速化
3. **容量問題の完全解決**：各段階で最適な環境を使用

1. **プロンプトファイルを活用**
   - 各段階の詳細な指示が含まれている
   - カスタマイズも可能

2. **中間成果物を確実に保存**
   - 各段階の出力は貴重な資料
   - 後から見返せるように整理

3. **Claude Codeの特性を活かす**
   - ファイル操作が得意
   - 長時間の作業も安定
   - エラー時の再実行が容易

4. **段階的アプローチの利点**
   - 品質管理がしやすい
   - 認知負荷が分散される
   - 成果が蓄積される

このガイドに従って実行すれば、チャット容量制限を気にせずに
高品質な才能生態学の記事を作成できます。