# 日本語クイックガイド

`coordination-kit` は、`Commander -> A.Shoulder -> fingers` で進める並列作業を、見える形で運用するためのテンプレート集です。

コードのフレームワークではなく、役割分担、可視化、引き継ぎ、審査のための運用キットだと考えると分かりやすいです。

## このリポジトリにあるもの

- `../../prompts/`: Commander と A.Shoulder を始動するときのプロンプト
- `../../templates/`: 運用ファイルの雛形
- `../`: 使い方ガイド

## 最初に読む順番

1. [英語版 Getting Started](../getting-started.md)
2. [Workspace Isolation](../guides/workspace-isolation.md)
3. [Directory Conventions](../reference/directory-conventions.md)
4. [Runbook](../guides/runbook.md)

## 10分で始める手順

1. キットを `assets/coordination-kit/` などの固定パスに置く
2. 実行用の作業領域を `trial-ops/` と `trial-runs/team-a/`, `trial-runs/team-b/` に分ける
3. `../../templates/PUBLIC_TRIAL_BRIEF_TEMPLATE.md` から共通ブリーフを作る
4. `../../prompts/COMMANDER_THREAD_PROMPT.md` で Commander を開始する
5. ユーザーが直接指示したいなら `../../prompts/SHOULDER_THREAD_PROMPT.md` で A.Shoulder を可視スレッドにする
6. 必要なテンプレートだけを実運用側にコピーする

## どのファイルをいつ使うか

- 全体の流れを知りたい: [Runbook](../guides/runbook.md)
- ディレクトリの責務を決めたい: [Directory Conventions](../reference/directory-conventions.md)
- 開始前の抜け漏れを見たい: [Bootstrap Checklist](../guides/bootstrap-checklist.md)
- 誰かに「このファイルを読んで作業して」と明示的に送る: `../../templates/COMMAND_DISPATCH_TEMPLATE.md`
- 人が別スレッドへ転送する文面を作る: `../../templates/SEND_READY_PROMPT_TEMPLATE.md`
- 中盤以降に担当を組み替える: `../../templates/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- 最終引き継ぎを固定フォーマットで残す: `../../templates/FINAL_HANDOFF_TEMPLATE.md`

## 重要な考え方

- ファイルを置いただけでは指示したことにならない
- チームごとの書き込み領域は分ける
- judge 向け説明と player 向け説明は主言語でそろえる
- `midpoint playable` は「通しで実演できる」状態を指す
- 中盤以降は、実装だけでなく検証、文書化、ローカライズ、handoff にも担当を再配分する

## 推奨ディレクトリ例

```text
your-project/
  assets/
    coordination-kit/
  trial-ops/
  trial-runs/
    team-a/
    team-b/
```

## 迷ったときの入口

- 新規導入: [英語版 Getting Started](../getting-started.md)
- 実運用: [Runbook](../guides/runbook.md)
- 公開前確認: [Publishing Checklist](../maintenance/publishing-checklist.md)
