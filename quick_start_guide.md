# Claude Code クイックスタートガイド

## すぐに試せるテストコマンド

### 1. プロジェクト構造の確認
```bash
claude-code "C:\ClaudeWork\talent-ecosystem-projectのディレクトリ構造を表示して、プロンプトファイルの概要を説明してください。"
```

### 2. 出力ディレクトリの準備
```bash
claude-code "C:\ClaudeWork\talent-ecosystem-project\outputsディレクトリを作成し、テスト用にtest_personサブディレクトリも作成してください。"
```

### 3. Stage 1Aのテスト実行（短縮版）
```
通常のClaudeチャットで実行：
「テスト実行：宮沢賢治の才能家系図を簡易的に作成します（10分版）。
Web検索で主要な関係者を3-4名特定し、
簡単な才能家系図を作成してください。」

→ 結果をコピーしてtest_stage1a.mdとして保存
```

### 4. Stage 2以降のテスト（Claude Code）
```bash
# 保存したファイルをClaude Codeで読み込み
claude-code "C:\ClaudeWork\talent-ecosystem-project\outputs\test_person\test_stage1a.mdを読み込んで、内容を要約してください。"

# Stage 2のテスト実行
claude-code "テスト：読み込んだStage 1Aの結果を基に、簡単な関係性分析を実施してtest_stage2.mdに保存。"
```

## 本格実行の準備チェックリスト

### ステップ1: 環境確認
- [ ] Claude Codeがインストールされている
- [ ] プロジェクトディレクトリにアクセスできる
- [ ] プロンプトファイルが全て存在する

### ステップ2: 対象人物の決定
- [ ] 調査したい人物を決定
- [ ] 基本的な情報（分野、時代）を把握
- [ ] 4-5時間の作業時間を確保

### ステップ3: ディレクトリ準備
```bash
# 人物名のディレクトリを作成（例：村上春樹の場合）
claude-code "C:\ClaudeWork\talent-ecosystem-project\outputs\murakami_harukiディレクトリを作成してください。"
```

### ステップ4: 実行開始
各Stageのコマンドを順番に実行

## トラブルシューティング

### よくある質問

**Q: Claude Codeと通常のClaudeの使い分けは？**
A: 
- **通常のClaude**：Web検索やリサーチが必要なStage 1A/1Bで使用
- **Claude Code**：ファイル操作が中心のStage 2-4で使用

※Claude Codeには検索機能がないため、この使い分けが重要です。

**Q: 通常のClaudeチャットとの違いは？**
A: 
- ファイルの読み書きが得意
- タスクごとに独立して実行（容量制限を回避）
- コマンドラインから実行

**Q: インストール方法は？**
A: Anthropicの公式ブログ（「Claude Code」で検索）を参照してください。

**Q: エラーが出ました**
A: 
1. ファイルパスが正しいか確認
2. ディレクトリが存在するか確認
3. Claude Codeが正しくインストールされているか確認

## 次のステップ

1. **テスト実行**
   - 通常ClaudeでStage 1Aテスト
   - Claude CodeでStage 2以降テスト

2. **本格的な人物を選定**
   - 情報が豊富な人物がおすすめ
   - 調査しやすい分野から開始

3. **ハイブリッド実行**
   - Stage 1A/1B：通常Claude（検索）
   - Stage 2-4：Claude Code（分析・執筆）

4. **成果物を確認**しながら進める

## サポート

問題が発生した場合：
1. エラーメッセージを確認
2. ファイルパスを再確認
3. 該当Stageのプロンプトファイルを確認
4. 必要に応じて、通常のClaudeチャットで相談

---

Claude Codeを使うことで、才能生態学プロジェクトが
より効率的で楽しいものになることを願っています！