# HE_ASDF — HalfEngineer AI Spec-Driven Development Framework

AIエージェントによるSpec-Driven Developmentのためのフレームワーク。

仕様を書いたらAIが作る。作ったら仕様に書き戻す。仕様は常に生きている。

## 特徴

- **Living Spec**: 仕様は書いたら終わりではない。実装中に判明した事実を書き戻す
- **必須確認チェックリスト**: PMが質問すべき項目をカテゴリ別に網羅
- **ユースケース単位のイテレーション**: 1UC = 1 orchestrate で粒度を管理
- **仕様フィードバック分類**: SPEC_GAP / SPEC_WRONG / SPEC_AMBIGUOUS で構造化
- **6フェーズ + 書き戻しサイクル**: 要件→設計→実装→レビュー→ドキュメント→コミット + 仕様への書き戻し

## レイヤー構成

| レイヤー | スコープ | ステータス |
|---|---|---|
| Strategy Layer | ロードマップ・チーム間調整 | 将来スコープ |
| **Execution Layer** | **1UCのorchestrate** | **v1（本テンプレート）** |
| Integration Layer | 結合・リリース・運用 | 将来スコープ |

## Spec管理レベル

**spec-anchored** — 仕様とコードを並行メンテし、ドリフトを検出・修正する。

arXiv論文「Spec-Driven Development: From Code to Contract in the Age of AI Coding Assistants」（2602.00180）の3レベル分類に基づく。

## ワークフロー

```
PO指示 → サイズ判定 → 計画提示 → PO承認 → 実行 → 結果報告 → PO承認 → 次フェーズ
```

| Phase | 担当 | 成果物 |
|---|---|---|
| 1. 要件定義 | PM | requirements.md |
| 2. 設計＋タスク分解 | Architect | design.md + tasks.md |
| 3. 実装＋テスト | Implementer | src/ + tests/ |
| 4. レビュー | Reviewer | review.md |
| 5. ドキュメント | Documenter | CHANGELOG, README等 |
| 6. コミット | Orchestrator | git commit |

Phase 3〜4で仕様との乖離が発見された場合、**仕様に書き戻す**（Living Specサイクル）。

## 使い方

1. このリポジトリをクローンする
2. `SPEC.md` にプロダクトの全体像とユースケースを記入する
3. `CLAUDE.md` の技術スタックとコマンドを自分のプロジェクトに合わせる
4. `/orchestrate {指示}` で開発を開始する

## コマンド一覧

| コマンド | 用途 |
|---|---|
| `/orchestrate {指示}` | 新機能開発のワークフロー起動 |
| `/bugfix {バグの説明}` | バグ修正ワークフロー起動 |
| `/resume` | セッション切断後の途中復帰 |
| `/change-request {変更内容}` | 実装途中の要件変更・追加対応 |
| `/status` | 現在の進捗をサマリー表示 |

## 経緯

このフレームワークは [halfengineer-sdd-lab](https://github.com/brave-clover/halfengineer-sdd-lab)（SDD v1〜v4）での実験を経て生まれた。

- v1〜v3: 仕様書テンプレートの試行錯誤
- v4: Agent Teams・Hooks・Custom Commands対応
- **HE_ASDF v1**: Living Spec（仕様書き戻し）・PM質問強化・ユースケース分解を追加。海外のSpec-Driven Development研究を取り込み、個人開発テンプレートからフレームワークに進化

詳細は[ブログ](https://note.com/halfeng202602)を参照。

## 参照文献

| タイトル | 出典 |
|---|---|
| Spec-Driven Development: From Code to Contract | arXiv 2602.00180 (2026) |
| How to Write a Good Spec for AI Agents | O'Reilly Radar (2026) |
| Spec-driven development: Unpacking one of 2025's key new practices | Thoughtworks (2025) |
| spec-kit | GitHub (2025) |
| Aligning SDD and Context Engineering for 2026 | WeBuild-AI (2025) |

## 注意

これは実験的なフレームワークです。AIが生成したコードの品質は人間が確認してください。

## ライセンス

MIT