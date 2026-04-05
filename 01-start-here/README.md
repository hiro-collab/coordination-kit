# Start Here

Use this file when you want to adopt `coordination-kit` in a real project.

This is the main user guide. Most users only need this file, the reference use case, the placement guide, and the runbook.

English comes first in this file. A Japanese mirror appears later in the same document.

## Quick Adoption

1. Put `coordination-kit` next to your project, or add it as a Git submodule.
2. Decide the exact kit path and the exact writable project paths.
3. Open both the project and the kit in a file-aware AI coding system.
4. Tell the AI to use `coordination-kit`, name the kit path, and restrict writes to project-side directories such as `./run-ops` and `./run-workspaces`.
   Ask it to confirm those read/write paths back before it creates anything.
5. Before real implementation starts, confirm that visible ownership, sign-off, and handoff files exist in the project.

Example instruction:

```text
The reusable coordination kit is at ../coordination-kit.
Before creating anything, confirm that you can read ../coordination-kit and that you will write only under ./run-ops and ./run-workspaces.
Do not create live run files in ../ or inside ../coordination-kit.
Write only inside this project, mainly under ./run-ops and ./run-workspaces.
Use coordination-kit for this project.
Act as Commander.
Set up Arm A and Arm B as team lanes.
Create `MISSION_BRIEF.md` and `INTEGRATION.md` first, then create node-local working-memory or log files, plus `VERIFICATION_RECORD.md` or `FINAL_HANDOFF.md` when needed.
Keep ownership explicit and do not sign off early.
```

## Use This Kit When

- one person or one top-level thread must supervise several agent lanes on the same task
- prompts alone are no longer enough and you need explicit files for handoff, verification, and integration
- you want reusable coordination assets that can be applied across many project runs

## Avoid It When

- one user and one agent can finish the task directly with no coordination overhead
- you are looking for a workflow engine, scheduler, or compute runtime
- your team will not maintain visible files or explicit dispatch messages

## One Concrete Example

The default example is a scoped software delivery run.

The user wants:

- one feature or change shipped
- API stability preserved
- parallel AI work without losing final control

The user should see:

- one lane leaning implementation-heavy
- another lane leaning verification or handoff-heavy
- visible files that show scope, status, evidence, and sign-off ownership

Read [reference-use-case.md](reference-use-case.md) for the concrete scenario.

## User Reading Path

Read these in order:

1. [../README.md](../README.md)
2. [reference-use-case.md](reference-use-case.md)
3. [project-placement.md](project-placement.md)
4. [../02-runbook/README.md](../02-runbook/README.md)

Read these only if needed:

- [../03-reference/README.md](../03-reference/README.md) for AI / system rules
- [../prompts/README.md](../prompts/README.md) when starting visible AI threads
- [../templates/README.md](../templates/README.md) when asking the AI to create live files

## First 15 Minutes

1. Confirm the kit path and writable project paths.
2. Create or confirm `run-ops/` and `run-workspaces/arm-*/`.
3. Create `MISSION_BRIEF.md` and `INTEGRATION.md`.
4. Start the Commander thread.
5. Start a visible Shoulder thread only if direct user steering is needed.
6. Dispatch the first visible tasks.
7. Confirm where verification and final sign-off will land.

## What You Should See

After the first setup pass, you should usually have:

- `MISSION_BRIEF.md` that states scope and finish conditions
- `INTEGRATION.md` as the shared integration file
- one or more `WORKING_MEMORY.<node>.md` or `LOG.<node>.md` files for active lanes
- `VERIFICATION_RECORD.md` or `FINAL_HANDOFF.md` before sign-off
- no live run files in the shared parent directory or back inside the kit

## Where Specific Questions Go

- path rules, writable boundaries, submodule vs sibling: [project-placement.md](project-placement.md)
- concrete adoption example: [reference-use-case.md](reference-use-case.md)
- live execution and checkpoints: [../02-runbook/README.md](../02-runbook/README.md)
- topology, protocol, and memory rules for AI or advanced operators: [../03-reference/README.md](../03-reference/README.md)

## Japanese

このファイルは、`coordination-kit` を実プロジェクトに導入するときの主な user guide です。

多くの user は、このファイル、代表ユースケース、配置ルール、runbook を読めば始められます。

## すぐ始める手順

1. `coordination-kit` を project の横に置くか、Git submodule として入れる
2. kit の実パスと、project 側の書き込み先を決める
3. project と kit の両方を file-aware な AI coding system で開く
4. `coordination-kit` を使うこと、kit の場所、書き込み境界を AI に伝える
   そのうえで、何か作る前に read path / write path を AI に復唱させる
5. 実装を始める前に、ownership、sign-off、handoff の visible file が project 側にできているか確認する

例:

```text
再利用する coordination kit は ../coordination-kit にある。
何か作る前に、../coordination-kit を読めることと、書き込みが ./run-ops と ./run-workspaces に限定されることを確認する。
live run file を ../ や ../coordination-kit の中には作らない。
書き込みはこの project 配下、主に ./run-ops と ./run-workspaces に限定する。
この project では coordination-kit を使う。
あなたは Commander として動く。
Arm A と Arm B を team lane として作る。
まず `MISSION_BRIEF.md` と `INTEGRATION.md` を作り、そのあと node ごとの working-memory か log、必要なら `VERIFICATION_RECORD.md` か `FINAL_HANDOFF.md` を作る。
ownership を明示し、途中で勝手に sign-off しない。
```

## このキットが向いている場面

- 1 人の人間や上位 thread が、複数の agent lane を同時に監督したい
- prompt だけでは足りず、handoff、verification、integration の visible file が欲しい
- project をまたいで再利用できる coordination 資産を持ちたい

## 向いていない場面

- 1 user と 1 agent でそのまま終わる小タスク
- workflow engine、scheduler、compute runtime を探している場合
- visible file や explicit dispatch を運用しない場合

## 代表ユースケース

標準の例は、スコープを絞ったソフトウェア変更です。

ユーザーの意図:

- 1 つの機能や変更を出したい
- API は壊したくない
- AI は並列で動かしたいが、最後の責任は 1 か所に残したい

ユーザーから見えるべきもの:

- ある lane は実装寄り
- 別の lane は verification や handoff 寄り
- scope、status、evidence、sign-off ownership が visible file で追える

具体例は [reference-use-case.md](reference-use-case.md) を見てください。

## ユーザー向けの読む順番

まずは次の順です。

1. [../README.md](../README.md)
2. [reference-use-case.md](reference-use-case.md)
3. [project-placement.md](project-placement.md)
4. [../02-runbook/README.md](../02-runbook/README.md)

必要になってから読むもの:

- [../03-reference/README.md](../03-reference/README.md): AI / system rule
- [../prompts/README.md](../prompts/README.md): visible AI thread を立てるとき
- [../templates/README.md](../templates/README.md): AI に live file を作らせるとき

## 最初の15分

1. kit path と writable path を確定する
2. `run-ops/` と `run-workspaces/arm-*/` を作るか確認する
3. `MISSION_BRIEF.md` と `INTEGRATION.md` を作る
4. Commander thread を始める
5. direct steering が必要なときだけ visible Shoulder thread を始める
6. 最初の visible task を dispatch する
7. verification と final sign-off の着地点を確認する

## 最初に見えるべきもの

最初の setup が通っていれば、たいてい次が見えるはずです。

- scope と finish condition を書いた `MISSION_BRIEF.md`
- shared integration file である `INTEGRATION.md`
- active lane の `WORKING_MEMORY.<node>.md` か `LOG.<node>.md`
- sign-off 前の `VERIFICATION_RECORD.md` か `FINAL_HANDOFF.md`
- shared な親階層や kit の中に live run file が増えていないこと

## どの疑問ならどこを見るか

- path ルール、writable boundary、submodule か sibling か: [project-placement.md](project-placement.md)
- 具体的な導入例: [reference-use-case.md](reference-use-case.md)
- 実行中の checkpoint と運用: [../02-runbook/README.md](../02-runbook/README.md)
- topology、protocol、memory の固定ルール: [../03-reference/README.md](../03-reference/README.md)
