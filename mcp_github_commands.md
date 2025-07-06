# MCP GitHub統合 - 実践的なコマンド例

## 1. プロジェクト初期化

### リポジトリ作成とクローン
```bash
# MCPのGitHubツールで実行
github:create_repository(
  name="talent-ecosystem-project",
  description="才能生態学：才能の発現と連鎖を記録するプロジェクト",
  private=true
)

# ローカルにクローン
claude-code "GitHubからtalent-ecosystem-projectをクローンして初期設定"
```

### 初期ファイルのプッシュ
```bash
# 既存ファイルをGitHubにプッシュ
github:push_files(
  owner="[あなたのユーザー名]",
  repo="talent-ecosystem-project",
  branch="main",
  files=[全プロンプトファイル],
  message="feat: 初期プロンプトとガイドを追加"
)
```

## 2. 記事作成ワークフロー

### Stage 1A 完了時
```python
# Claude内で実行
"""
以下のタスクを実行：
1. Stage 1Aの結果をGitHubにコミット
2. ファイル: outputs/utada_hikaru/stage1a_mapping.md
3. ブランチ: feature/utada-hikaru
4. コミットメッセージ: 'feat(utada): Stage 1A 才能家系図完成'
"""

# 実際のMCPコマンド
github:create_branch(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  branch="feature/utada-hikaru"
)

github:create_or_update_file(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  path="outputs/utada_hikaru/stage1a_mapping.md",
  content="[Stage 1Aの内容]",
  message="feat(utada): Stage 1A 才能家系図完成",
  branch="feature/utada-hikaru"
)
```

### 全Stage完了後
```python
# プルリクエスト作成
github:create_pull_request(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  title="feat: 宇多田ヒカルの才能生態学記事",
  head="feature/utada-hikaru",
  base="main",
  body="""
  ## 概要
  宇多田ヒカルの才能生態学記事を作成しました。

  ## 完成した成果物
  - [x] Stage 1A: 才能家系図
  - [x] Stage 1B: 戦略的深掘り調査
  - [x] Stage 2: 関係性分析
  - [x] Stage 3: 記事構成
  - [x] Stage 4: 最終記事（5,234文字）

  ## 主要な発見
  - 藤圭子からの音楽的DNA継承
  - 三宅彰との出会いによる才能開花
  - 日米文化の架け橋としての役割

  ## チェックリスト
  - [x] 文字数は適切か（3500-7000字）
  - [x] 才能家系図は明確か
  - [x] 実用的な洞察があるか
  - [x] 参考文献は記載されているか
  """
)
```

## 3. プロンプト改善フロー

### 改善案の作成
```python
# 改善ブランチで作業
github:create_branch(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  branch="improve/stage1a-music-focus"
)

# 改善版プロンプトを作成
github:create_or_update_file(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  path="prompts/variants/stage1a_mapping_music.md",
  content="[音楽特化版のプロンプト]",
  message="feat: 音楽分野特化のStage 1Aプロンプト追加",
  branch="improve/stage1a-music-focus"
)
```

## 4. 分析とパターン発見

### 月次分析の実行
```python
# すべての完成記事を分析
"""
タスク：outputs/内のすべてのfinal_article.mdを分析し、
以下を抽出してGitHubにコミット：
1. 共通する才能発掘パターン
2. 効果的な構成パターン
3. 新しい法則の発見
保存先: analytics/2025_01_patterns.md
"""

# 分析結果をコミット
github:create_or_update_file(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  path="analytics/2025_01_patterns.md",
  content="[分析結果]",
  message="docs: 2025年1月の才能パターン分析",
  branch="main"
)
```

## 5. Issue管理

### 新規記事のIssue作成
```python
github:create_issue(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  title="記事作成: 村上春樹",
  body="""
  ## 対象人物
  - **名前**: 村上春樹
  - **分野**: 文学（小説家・翻訳家）
  - **選定理由**: 翻訳を通じた才能の相互影響が興味深い

  ## 作業計画
  - [ ] Stage 1A: 才能家系図作成
  - [ ] Stage 1B: 戦略的深掘り（レイモンド・カーヴァー等）
  - [ ] Stage 2: 関係性分析
  - [ ] Stage 3: 記事構成
  - [ ] Stage 4: 執筆

  ## 重点調査項目
  - ジャズ喫茶時代の影響
  - アメリカ文学との出会い
  - 翻訳活動と創作の相互影響

  担当: @[ユーザー名]
  予定完了日: 2025/01/20
  """,
  labels=["新規記事", "文学"],
  assignees=["[ユーザー名]"]
)
```

### 改善提案のIssue
```python
github:create_issue(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  title="提案: Stage 2の分析深度を向上",
  body="""
  ## 背景
  現在のStage 2分析で、循環構造の発見率が低い

  ## 提案内容
  1. 時系列分析の強化
  2. 逆方向影響の積極的探索
  3. インタビュー記事の重点活用

  ## 期待効果
  - 循環構造の発見率向上
  - より深い洞察の獲得
  """,
  labels=["改善提案", "プロンプト"]
)
```

## 6. 自動化スクリプト

### 品質チェックの自動化
```python
# .github/workflows/quality-check.yml の内容を作成
github:create_or_update_file(
  owner="[ユーザー名]",
  repo="talent-ecosystem-project",
  path=".github/workflows/quality-check.yml",
  content="""
name: 記事品質チェック
on:
  pull_request:
    paths:
      - 'outputs/*/final_article.md'

jobs:
  quality-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      
      - name: 文字数チェック
        run: |
          for file in outputs/*/final_article.md; do
            count=$(wc -m < "$file")
            if [ $count -lt 2500 ] || [ $count -gt 10000 ]; then
              echo "❌ $file: 文字数が範囲外 ($count文字)"
              exit 1
            else
              echo "✅ $file: $count文字"
            fi
          done
      
      - name: 必須要素チェック
        run: |
          for file in outputs/*/final_article.md; do
            echo "Checking $file..."
            grep -q "才能家系図\\|才能生態系マップ" "$file" || echo "⚠️ 家系図が見つかりません"
            grep -q "参考文献" "$file" || echo "⚠️ 参考文献が見つかりません"
          done
  """,
  message="ci: 品質チェックワークフローを追加",
  branch="main"
)
```

## 7. コラボレーション例

### レビュー依頼
```python
# プルリクエストにレビュアーを追加
# （プルリクエスト作成後）
"作成したPRにレビュアーを追加し、以下のコメントを投稿：
'@reviewer_name この記事のレビューをお願いします。
特に以下の点についてフィードバックをいただけますか：
1. 才能発掘者の描写は適切か
2. 循環構造は明確に伝わるか
3. 実用的な洞察は十分か'"
```

## 8. バックアップとアーカイブ

### 定期バックアップ
```python
# 月次でタグを作成
"2025年1月の全成果物が完成したので、
v2025.01 タグを作成し、リリースノートを追加：
- 完成記事: 3本
- 新規プロンプト: 2種
- 発見したパターン: 5個"
```

## 効果測定

### 導入前後の比較
| 項目 | 導入前 | 導入後 |
|------|--------|--------|
| 1記事の作成時間 | 5-6時間 | 4-5時間 |
| エラー回復時間 | 1-2時間 | 10-15分 |
| 品質の安定性 | 70% | 95% |
| 再利用可能性 | 低 | 高 |
| コラボレーション | 困難 | 容易 |

### ROI（投資対効果）
- **初期投資**: セットアップ2-3時間
- **回収期間**: 3-4記事で元が取れる
- **長期効果**: 作業効率30%向上

このように、MCP GitHubツールを活用することで、
才能生態学プロジェクトは格段に効率化・高品質化されます。