# HE_ASDF — HalfEngineer AI Spec-Driven Development Framework

AI Spec-Driven Developmentのためのフレームワークテンプレート。

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

spec-anchored（arXiv 2602.00180 の3レベル分類に基づく）

## 使い方

1. このリポジトリをクローンする
2. SPEC.md にプロダクトの全体像を記入する
3. CLAUDE.md の技術スタックとコマンドを自分のプロジェクトに合わせる
4. `/orchestrate {指示}` で開発を開始する

---

# halfengineer-sdd-lab（旧README）

非エンジニアがAIに開発を丸投げするための実験テンプレート。

「仕様書を書いたらAIが作ってくれる」を本気で試してみた記録です。
筆者が勝手にスペック駆動開発（SDD）と呼んでいます。

実績：このテンプレートで米国株損益管理ツールとTODOアプリを開発。コードは1行も書いてない。

### 従来のAI開発との違い

| | チャットベース | SDD |
|---|---|---|
| 指示の出し方 | その場でプロンプトを書く | 事前に仕様書を用意する |
| 品質の再現性 | 人とプロンプト次第 | テンプレートで標準化 |
| 承認フロー | なし（AIが自走） | planning → approval → execution |
| 対象ユーザー | エンジニア | PO/PM（非エンジニア含む） |

### ワークフロー（6フェーズ）

1. 要件定義（PMエージェント）
2. 設計＋タスク分解（Architectエージェント）
3. 実装＋テスト（Implementerエージェント）— Agent Teamsで並列実行可能
4. レビュー（Reviewerエージェント）
5. ドキュメント（Documenterエージェント）
6. コミット整理

## v4の主な変更点

- **CLAUDE.md**: プロジェクトメモリとして再設計（Claude Codeが毎回自動読み込み）
- **Hooks**: コード完成後のテスト自動実行、コミット前のバグ記録チェック、フェーズ完了時の記録
- **Custom Slash Commands**: /phase-review、/phase-test、/status を追加
- **Agent Teams**: 独立タスクの並列実行に対応
- **バグ記録の強制化**: 行動原則 + レビュー + Hooks の三重チェック

## 使い方

1. テンプレートをプロジェクトにコピー
2. `CLAUDE.md` を自分のプロジェクトに合わせて編集
3. Claude Code で `/orchestrate {やりたいこと}` を実行

## ブログ

- [① AI開発、思ったほど楽じゃなかった話](https://note.com/halfeng202602/n/na8fbe4649f0e)
- [② スペック駆動開発にたどり着くまで](https://note.com/halfeng202602/n/n9895c4570053)
- [③ テンプレートv3、検証してみた](https://note.com/halfeng202602/n/na931d69cb82e)
- [④ テンプレv4、シェフが同時に動き出した](https://note.com/halfeng202602/n/nc35e1335e4cd)

## 注意

これは個人の実験プロジェクトです。AIが生成したコードの品質は人間が確認してください。
