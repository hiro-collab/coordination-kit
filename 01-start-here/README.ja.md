# 日本語クイックガイド

`coordination-kit` は、`Commander -> A.Shoulder -> Thumb / Inddy / Middy / Ringy / Pinky` で進める並列作業を、見える形で運用するためのテンプレート集です。

コードのフレームワークではなく、役割分担、可視化、引き継ぎ、審査のための運用キットだと考えると分かりやすいです。

このフォルダでは、まずこの `README.ja.md` か [README.md](README.md) を読んでから次へ進む想定です。

## このリポジトリの見方

- `../README.md`: リポジトリ全体の入口
- `../01-start-here/`: 導入と初期設定
- `../02-run-a-trial/`: 実行中の運用ルール
- `../03-reference/`: 固定ルールと振り返り知見
- `../04-maintainers/`: 公開や保守用の資料
- `../prompts/`: Commander と A.Shoulder を始動するときのプロンプト
- `../templates/`: 実運用にコピーして使うテンプレート群

## 最初に読む順番

1. [英語版 Getting Started](README.md)
2. [Workspace Isolation](workspace-isolation.md)
3. [Runbook](../02-run-a-trial/README.md)
4. [Reference](../03-reference/README.md)

## 10分で始める手順

1. キットを `assets/coordination-kit/` などの固定パスに置く
2. 実行用の作業領域を `trial-ops/` と `trial-runs/team-a/`, `trial-runs/team-b/` に分ける
3. `../templates/01-setup/PUBLIC_TRIAL_BRIEF_TEMPLATE.md` から共通ブリーフを作る
4. `../prompts/COMMANDER_THREAD_PROMPT.md` で Commander を開始する
5. ユーザーが直接指示したいなら `../prompts/SHOULDER_THREAD_PROMPT.md` で A.Shoulder を可視スレッドにする
6. `../templates/README.md` を見て、必要なテンプレートだけを実運用側にコピーする

## どのフォルダに何があるか

- `../templates/01-setup/`: 実行前に作る基本ファイル
- `../templates/02-dispatch/`: 誰に何を読ませて動かすかの指示系
- `../templates/03-checkpoints/`: 中間チェック、再配分、検証記録
- `../templates/04-handoff/`: 提出、審査、最終引き継ぎ

この分け方にしているので、「どの段階で使う書類か」がフォルダ名だけでも分かるはずです。

## finger 名の標準

finger を使う場合は、役割名を次で固定します。

- `Thumb`
- `Inddy`
- `Middy`
- `Ringy`
- `Pinky`

`finger-1` のような番号だけよりも、共有ノート、タスクカード、進捗報告で誰がどのレーンか追いやすくなります。

## どのファイルをいつ使うか

- 全体の流れを知りたい: [Runbook](../02-run-a-trial/README.md)
- ディレクトリの責務を決めたい: [Directory Conventions](../03-reference/directory-conventions.md)
- 開始前の抜け漏れを見たい: [Bootstrap Checklist](../02-run-a-trial/bootstrap-checklist.md)
- 誰かに「このファイルを読んで作業して」と明示的に送る: `../templates/02-dispatch/COMMAND_DISPATCH_TEMPLATE.md`
- 人が別スレッドへ転送する文面を作る: `../templates/02-dispatch/SEND_READY_PROMPT_TEMPLATE.md`
- 中盤以降に担当を組み替える: `../templates/03-checkpoints/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- 最終引き継ぎを固定フォーマットで残す: `../templates/04-handoff/FINAL_HANDOFF_TEMPLATE.md`
- 審査の記録を残す: `../templates/04-handoff/GAME_JUDGING_SCORECARD_TEMPLATE.md`

## 日本語運用で意識したい点

- judge 向けと player 向けの説明は同じ主言語でそろえる
- ルール説明はゲーム開始直後に見える場所へ置く
- `midpoint playable` は「たぶん動く」ではなく「通しで見せられる」
- ファイルを書いただけでは指示にならないので、読む相手に明示的に送る
- 中盤以降は実装だけでなく、検証、文書化、ローカライズ、handoff にも担当を配る

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

- 新規導入: [英語版 Getting Started](README.md)
- 実運用: [Runbook](../02-run-a-trial/README.md)
- 公開前確認: [Publishing Checklist](../04-maintainers/publishing-checklist.md)
