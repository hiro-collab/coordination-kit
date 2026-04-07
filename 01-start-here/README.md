# Start Here

Use this file when you want to adopt `coordination-kit` in a real project.

This is the main user guide. Most users only need this file, the reference use case, the placement guide, and the runbook.

The root `README.md` already gives the first request pattern for the AI. This file is for the project-side checks and adoption decisions around that first request.

English comes first in this file. A Japanese mirror appears later in the same document.

## Quick Adoption

1. Put `coordination-kit` next to your project, or add it as a Git submodule.
2. Decide the exact kit path and the exact writable project paths.
3. Open both the project and the kit in a file-aware AI coding system, but start the session from the project root.
4. Start with the root `README.md` request pattern: tell the AI where the kit is, ask it to follow the kit, and tell it what work you want help with.
5. Then confirm the exact project-side read/write paths before it creates anything.
6. Before real implementation starts, confirm that visible ownership, sign-off, and handoff files exist in the project.

Use the root `README.md` request pattern first, then confirm the exact project-side checks in this file.

## User Reading Path

Read these in order:

1. [../README.md](../README.md) if you have not read it yet
2. [reference-use-case.md](reference-use-case.md)
3. [project-placement.md](project-placement.md)
4. [../02-runbook/README.md](../02-runbook/README.md)

Read these only if needed:

- [../03-reference/README.md](../03-reference/README.md) for AI / system rules
- [../03-reference/profile-inheritance/README.md](../03-reference/profile-inheritance/README.md) when a team wants to carry behavior forward across runs
- [../prompts/README.md](../prompts/README.md) when starting visible AI threads
- [../templates/README.md](../templates/README.md) when asking the AI to create live files

## First 15 Minutes

1. Confirm the kit path and writable project paths.
2. Create or confirm `run-ops/` and `run-workspaces/arm-*/`.
3. Create `MISSION_BRIEF.md`, `SHARED_NOTE.md`, and `INTEGRATION.md`.
4. Start the Commander thread.
5. Start a visible Shoulder thread only if direct user steering is needed.
6. Dispatch the first visible tasks.
7. Confirm where verification and final sign-off will land.

## What You Should See

After the first setup pass, you should usually have:

- `MISSION_BRIEF.md` that states scope and finish conditions
- `SHARED_NOTE.md` for shared interfaces, file ownership, and active assumptions
- `INTEGRATION.md` as the shared integration file
- one or more `WORKING_MEMORY.<node>.md` or `LOG.<node>.md` files for active lanes
- `VERIFICATION_RECORD.md` or `FINAL_HANDOFF.md` before sign-off
- no live run files in the shared parent directory or back inside the kit

## Where Specific Questions Go

- path rules, writable boundaries, submodule vs sibling: [project-placement.md](project-placement.md)
- concrete adoption example: [reference-use-case.md](reference-use-case.md)
- live execution and checkpoints: [../02-runbook/README.md](../02-runbook/README.md)
- topology, protocol, and memory rules for AI or advanced operators: [../03-reference/README.md](../03-reference/README.md)
- durable profile carry-forward rules: [../03-reference/profile-inheritance/README.md](../03-reference/profile-inheritance/README.md)

## Japanese

このファイルは、`coordination-kit` を実プロジェクトに導入するときの主な user guide です。

多くの user は、このファイル、代表ユースケース、配置ルール、runbook を読めば始められます。

## すぐ始める手順

1. `coordination-kit` を project の横に置くか、Git submodule として入れる
2. kit の実パスと、project 側の書き込み先を決める
3. project と kit の両方を file-aware な AI coding system で開くが、session の起点は project root にする
4. root の [../README.md](../README.md) にある最初の依頼パターンを使い、kit の場所、kit に従うこと、手伝ってほしい作業内容を AI に伝える
5. そのあとで、何か作る前に exact な read path / write path を AI に復唱させる
6. 実装を始める前に、ownership、sign-off、handoff の visible file が project 側にできているか確認する

最初の AI への依頼は root の [../README.md](../README.md) にあるパターンを使い、このファイルでは project 側の exact な確認事項を詰めます。

## ユーザー向けの読む順番

まずは次の順です。

1. [../README.md](../README.md) をまだ読んでいなければ先に読む
2. [reference-use-case.md](reference-use-case.md)
3. [project-placement.md](project-placement.md)
4. [../02-runbook/README.md](../02-runbook/README.md)

必要になってから読むもの:

- [../03-reference/README.md](../03-reference/README.md): AI / system rule
- [../03-reference/profile-inheritance/README.md](../03-reference/profile-inheritance/README.md): team の behavior を run をまたいで carry forward したいとき
- [../prompts/README.md](../prompts/README.md): visible AI thread を立てるとき
- [../templates/README.md](../templates/README.md): AI に live file を作らせるとき

## 最初の15分

1. kit path と writable path を確定する
2. `run-ops/` と `run-workspaces/arm-*/` を作るか確認する
3. `MISSION_BRIEF.md`、`SHARED_NOTE.md`、`INTEGRATION.md` を作る
4. Commander thread を始める
5. direct steering が必要なときだけ visible Shoulder thread を始める
6. 最初の visible task を dispatch する
7. verification と final sign-off の着地点を確認する

## 最初に見えるべきもの

最初の setup が通っていれば、たいてい次が見えるはずです。

- scope と finish condition を書いた `MISSION_BRIEF.md`
- shared interface、file ownership、active assumption をまとめる `SHARED_NOTE.md`
- shared integration file である `INTEGRATION.md`
- active lane の `WORKING_MEMORY.<node>.md` か `LOG.<node>.md`
- sign-off 前の `VERIFICATION_RECORD.md` か `FINAL_HANDOFF.md`
- shared な親階層や kit の中に live run file が増えていないこと

## どの疑問ならどこを見るか

- path ルール、writable boundary、submodule か sibling か: [project-placement.md](project-placement.md)
- 具体的な導入例: [reference-use-case.md](reference-use-case.md)
- 実行中の checkpoint と運用: [../02-runbook/README.md](../02-runbook/README.md)
- topology、protocol、memory の固定ルール: [../03-reference/README.md](../03-reference/README.md)
- durable profile の carry-forward ルール: [../03-reference/profile-inheritance/README.md](../03-reference/profile-inheritance/README.md)
