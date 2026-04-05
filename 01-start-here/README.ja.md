# 日本語クイックガイド

`coordination-kit` は、`Commander -> Arms -> Shoulder / Elbow / Fingers` で進める階層型マルチエージェント運用を、見える形で管理するためのテンプレート集です。

コードのフレームワークではなく、役割分担、可視化、引き継ぎ、評価のための運用キットだと考えると分かりやすいです。

このフォルダでは、まずこの `README.ja.md` か [README.md](README.md) を読んでから次へ進む想定です。

## このリポジトリの見方

- `../README.md`: リポジトリ全体の入口
- `../01-start-here/`: 導入と初期設定
- `../02-run-a-trial/`: 実行中の運用ルール
- `../03-reference/`: 汎用トポロジ、memory モデル、固定ルール、振り返り知見
- `../04-maintainers/`: 公開や保守用の資料
- `../prompts/`: Commander と Shoulder を始動するときのプロンプト
- `../templates/`: 実運用にコピーして使うテンプレート群

## 最初に読む順番

1. [英語版 Installation](README.md)
2. [Agent Topology](../03-reference/agent-topology.md)
3. [Memory and Personality](../03-reference/memory-and-personality.md)
4. [Workspace Isolation](workspace-isolation.md)
5. [Runbook](../02-run-a-trial/README.md)
6. [Reference](../03-reference/README.md)

## 10分で始める手順

1. キットを `assets/coordination-kit/` などの固定パスに置く
2. `A.Shoulder`, `A.Indy` のような node id と階層を決める
3. 必要なら `PERSONALITY` と `WORKING_MEMORY` の分離方針を決める
4. 実行用の作業領域を `trial-ops/` と `trial-runs/arm-a/`, `trial-runs/arm-b/` のように分ける
5. `../templates/01-setup/MISSION_BRIEF_TEMPLATE.md` から共通ブリーフを作る
6. 必要なら `../templates/01-setup/PERSONALITY_TEMPLATE.md` から personality ファイルを作る
7. `../prompts/COMMANDER_THREAD_PROMPT.md` で Commander を開始する
8. ユーザーが直接指示したいなら `../prompts/SHOULDER_THREAD_PROMPT.md` で Shoulder を可視スレッドにする
9. `../templates/README.md` を見て、必要なテンプレートだけを実運用側にコピーする

## node 名の標準

Arm を含めた compact id を基本にします。

- `A.Shoulder`
- `A.Elbow`
- `A.Thumb`
- `A.Indy`
- `A.Middy`
- `A.Ringy`
- `A.Pinky`

finger を 5 本使う場合のローカル名は次です。

- `Thumb`
- `Indy`
- `Middy`
- `Ringy`
- `Pinky`

`finger-1` のような番号だけよりも、共有ノート、タスクカード、進捗報告で誰がどのレーンか追いやすくなります。

名前は役割ではありません。`Indy` が explore をやることもあれば、verify や integrate をやることもあります。

## mode の扱い

`Explore / Verify / Integrate` は便利な代表例ですが、固定クラスではありません。

必要なら別の mode 名を使って構いません。大事なのは、いま何を重視している node なのかを明示することです。

## どのフォルダに何があるか

- `../templates/01-setup/`: 実行前に作る基本ファイル
- `../templates/02-dispatch/`: 誰に何を読ませて動かすかの指示系
- `../templates/03-checkpoints/`: 中間チェック、再配分、検証記録
- `../templates/04-handoff/`: 提出、評価、最終引き継ぎ

この分け方にしているので、「どの段階で使う書類か」がフォルダ名だけでも分かるはずです。

## どのファイルをいつ使うか

- 全体の流れを知りたい: [Runbook](../02-run-a-trial/README.md)
- 汎用トポロジを先に確認したい: [Agent Topology](../03-reference/agent-topology.md)
- personality と working memory の分離を確認したい: [Memory and Personality](../03-reference/memory-and-personality.md)
- ディレクトリの責務を決めたい: [Directory Conventions](../03-reference/directory-conventions.md)
- 開始前の抜け漏れを見たい: [Bootstrap Checklist](../02-run-a-trial/bootstrap-checklist.md)
- 誰かに「このファイルを読んで作業して」と明示的に送る: `../templates/02-dispatch/COMMAND_DISPATCH_TEMPLATE.md`
- 人が別スレッドへ転送する文面を作る: `../templates/02-dispatch/SEND_READY_PROMPT_TEMPLATE.md`
- 中盤以降に担当を組み替える: `../templates/03-checkpoints/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- 最終引き継ぎを固定フォーマットで残す: `../templates/04-handoff/FINAL_HANDOFF_TEMPLATE.md`
- 評価の記録を残す: `../templates/04-handoff/GAME_JUDGING_SCORECARD_TEMPLATE.md`

## 日本語運用で意識したい点

- judge 向けと player 向けの説明は同じ主言語でそろえる
- ルール説明は開始直後に見える場所へ置く
- `midpoint playable` は「たぶん動く」ではなく「通しで見せられる」
- ファイルを書いただけでは指示にならないので、読む相手に明示的に送る
- 中盤以降は実装だけでなく、検証、文書化、ローカライズ、handoff にも担当を配る
- `PERSONALITY` と `WORKING_MEMORY` は混ぜない
- personality は自動学習させず、必要なら明示的に更新する

## 推奨ディレクトリ例

```text
your-project/
  assets/
    coordination-kit/
  trial-ops/
  trial-runs/
    arm-a/
    arm-b/
```

## 迷ったときの入口

- 新規導入: [英語版 Installation](README.md)
- 実運用: [Runbook](../02-run-a-trial/README.md)
- 公開前確認: [Publishing Checklist](../04-maintainers/publishing-checklist.md)
