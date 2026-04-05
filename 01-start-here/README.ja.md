# 日本語スタートガイド

`coordination-kit` は、`Commander -> Arms -> Shoulder / Elbow / Fingers` で進める階層型マルチエージェント運用を、見える形で管理するためのテンプレート集です。

コードのフレームワークではなく、役割分担、可視化、引き継ぎ、評価のための運用キットだと考えると分かりやすいです。

このフォルダでは、まずこの `README.ja.md` か [README.md](README.md) を読んでから次へ進む想定です。

## このキットが向いている場面

- 1 人の人間や上位 thread が、複数の agent lane を同時に監督したい
- prompt だけでは足りず、handoff、検証、統合のための visible file が欲しい
- プロジェクトごとに再利用できる coordination 資産を持ちたい

## このキットが向いていない場面

- 1 agent と 1 user でそのまま終わる小タスク
- workflow engine や scheduler、runtime を探している場合
- visible file や explicit dispatch を運用するつもりがない場合

## 代表ユースケース

この repo の front-door 例は「まとまったソフトウェア変更を、実装 lane と検証 lane に分けて進める run」です。
詳しくは [reference-use-case.ja.md](reference-use-case.ja.md) を読むと、何に使うキットなのかが早く掴めます。

## このリポジトリの見方

- `../README.md`: リポジトリ全体の入口
- `../01-start-here/`: 導入と初期設定
- `../02-runbook/`: 実行中の運用ルール
- `../03-reference/`: 汎用トポロジ、memory モデル、固定ルール、振り返り知見
- `../04-maintainers/`: 公開や保守用の資料
- `../prompts/`: Commander と Shoulder を始動するときのプロンプト
- `../templates/`: 実運用にコピーして使うテンプレート群

## 最初に読む順番

1. [英語版 Start Here](README.md)
2. [代表ユースケース](reference-use-case.ja.md)
3. [Agent Topology](../03-reference/agent-topology.md)
4. [Memory and Personality](../03-reference/memory-and-personality.md)
5. [git-usage.md](git-usage.md)
6. [Workspace Isolation](workspace-isolation.md)
7. [Runbook](../02-runbook/README.md)
8. [Reference](../03-reference/README.md)

## 10分で始める手順

1. キットを `assets/coordination-kit/` などの固定パスに置く
2. `A.Shoulder`, `A.Indy` のような node id と階層を決める
3. 必要なら `PERSONALITY` と `WORKING_MEMORY` の分離方針を決める
4. [git-usage.md](git-usage.md) を見て、どう配置するかを決める
5. 実行用の作業領域を `run-ops/` と `run-workspaces/arm-a/`, `run-workspaces/arm-b/` のように分ける
6. `../templates/01-setup/MISSION_BRIEF_TEMPLATE.md` から共通ブリーフを作る
7. 必要なら `../templates/01-setup/PERSONALITY_TEMPLATE.md` から personality ファイルを作る
8. `../prompts/COMMANDER_THREAD_PROMPT.md` で Commander を開始する
9. ユーザーが直接指示したいなら `../prompts/SHOULDER_THREAD_PROMPT.md` で Shoulder を可視スレッドにする
10. `../templates/README.md` を見て、必要なテンプレートだけを実運用側にコピーする

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

- 全体の流れを知りたい: [Runbook](../02-runbook/README.md)
- 汎用トポロジを先に確認したい: [Agent Topology](../03-reference/agent-topology.md)
- personality と working memory の分離を確認したい: [Memory and Personality](../03-reference/memory-and-personality.md)
- ディレクトリの責務を決めたい: [Directory Conventions](../03-reference/directory-conventions.md)
- 開始前の抜け漏れを見たい: [Bootstrap Checklist](../02-runbook/bootstrap-checklist.md)
- 誰かに「このファイルを読んで作業して」と明示的に送る: `../templates/02-dispatch/COMMAND_DISPATCH_TEMPLATE.md`
- 人が別スレッドへ転送する文面を作る: `../templates/02-dispatch/SEND_READY_PROMPT_TEMPLATE.md`
- 中盤以降に担当を組み替える: `../templates/03-checkpoints/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- 最終引き継ぎを固定フォーマットで残す: `../templates/04-handoff/FINAL_HANDOFF_TEMPLATE.md`
- 比較型 browser-game trial の評価記録を残す: `../templates/04-handoff/GAME_JUDGING_SCORECARD_TEMPLATE.md`

## 日本語運用で意識したい点

- reviewer 向けや end-user 向けの説明がある run では、同じ主言語でそろえる
- ルール説明は開始直後に見える場所へ置く
- demo checkpoint を置く run では、`midpoint playable` を「たぶん動く」ではなく「通しで見せられる」の意味で使う
- ファイルを書いただけでは指示にならないので、読む相手に明示的に送る
- 中盤以降は実装だけでなく、検証、文書化、ローカライズ、handoff にも担当を配る
- `PERSONALITY` と `WORKING_MEMORY` は混ぜない
- personality は自動学習させず、必要なら明示的に更新する

## 推奨ディレクトリ例

```text
your-project/
  assets/
    coordination-kit/
  run-ops/
  run-workspaces/
    arm-a/
    arm-b/
```

比較実験を強調したい run なら、`trial-ops/` や `trial-runs/` という名前でも構いません。

## 迷ったときの入口

- 新規導入: [英語版 Start Here](README.md)
- 代表ユースケース: [reference-use-case.ja.md](reference-use-case.ja.md)
- 実運用: [Runbook](../02-runbook/README.md)
- 公開前確認: [Publishing Checklist](../04-maintainers/publishing-checklist.md)
