# Start Here

Use this guide when you want to adopt `coordination-kit` in another workspace and decide whether it is the right tool.

This repository is documentation and templates for visible multi-agent operations. There is no package-manager install step and no hidden execution runtime.

If you are browsing the repository for the first time, read this file before any deeper file in this folder.

English comes first in this file. A Japanese mirror and extra Japanese operator notes appear later in the same document.

## Use This Kit When

- one person or one top-level thread must supervise several agent lanes on the same task
- prompts alone are no longer enough and you need explicit files for handoff, verification, and integration
- you want reusable coordination assets that can be copied into many project runs

## Avoid It When

- one agent and one user can finish the task directly with no coordination overhead
- you are looking for an execution framework, scheduler, or event runtime
- your team will not maintain visible files or explicit dispatch messages

## One Concrete Example

The default example for this repository is a scoped software delivery run:

- `Commander` owns the mission brief and final integration.
- `Arm A` and `Arm B` are stable team identities, not fixed departments.
- In this example, current assignments put more implementation work in `Arm A` and more verification or handoff work in `Arm B`.
- Nodes such as `A.Indy` and `B.Thumb` execute concrete subtasks with visible status updates.

Read [reference-use-case.md](reference-use-case.md) before going deeper if you want to see the model in a real scenario.

## Read In This Order

1. [../README.md](../README.md)
2. [reference-use-case.md](reference-use-case.md)
3. [../03-reference/agent-topology.md](../03-reference/agent-topology.md)
4. [../03-reference/coordination-primitives.md](../03-reference/coordination-primitives.md)
5. [../03-reference/memory-and-personality.md](../03-reference/memory-and-personality.md)
6. [git-usage.md](git-usage.md)
7. [workspace-isolation.md](workspace-isolation.md)
8. [../02-runbook/README.md](../02-runbook/README.md)
9. [../03-reference/README.md](../03-reference/README.md)

## Folder Map

- `../01-start-here/`: first-time adoption and environment setup
- `../02-runbook/`: live execution guidance and preflight checks
- `../03-reference/`: generic topology, memory model, stable rules, and lessons learned
- `../04-maintainers/`: release and publishing tasks
- `../prompts/`: startup prompts for Commander and Shoulder threads
- `../templates/`: copyable templates grouped by run phase

## Standard Node IDs

Use compact IDs that preserve the Arm relationship:

- `A.Shoulder`
- `A.Elbow`
- `A.Thumb`
- `A.Indy`
- `A.Middy`
- `A.Ringy`
- `A.Pinky`

When an arm activates five finger lanes, use these local finger names consistently:

- `Thumb`
- `Indy`
- `Middy`
- `Ringy`
- `Pinky`

Use those names in task cards, file ownership, status updates, and handoff notes so the relationship between lanes stays visible.

Names are identifiers, not fixed roles. A node may explore, verify, integrate, or implement depending on the current task.

## Modes

If you use mode labels, treat them as explicit task emphasis rather than permanent classes.

Common examples are:

- `Explore`
- `Verify`
- `Integrate`

These are examples, not a closed mandatory set.

## Recommended Options

### Option 1: Copy The Directory

Use this when you want a local editable copy inside a project and do not need automatic upstream tracking.

1. Copy `coordination-kit/` into your target workspace.
2. Keep it under a stable path such as `assets/coordination-kit/`.
3. Copy only the prompts and templates you need into the live run workspace.

### Option 2: Clone As A Standalone Reference Repo

Use this when you want to keep the kit versioned separately from the product repository.

Recommended placement: keep this clone outside the product repo as a sibling directory, not as a plain nested clone inside another `.git` working tree.

```bash
git clone <repo-url> coordination-kit
```

Then keep run-specific files outside this repository and copy prompts or templates into the active project.

### Option 3: Add As A Git Submodule

Use this when the product repository should pin a kit revision and update it explicitly.

```bash
git submodule add <repo-url> assets/coordination-kit
git submodule update --init --recursive
```

## First 15 Minutes

1. Decide where the reusable kit will live.
2. Define the active topology and node IDs with [../03-reference/agent-topology.md](../03-reference/agent-topology.md).
3. Read the coordination model in [../03-reference/coordination-primitives.md](../03-reference/coordination-primitives.md).
4. Decide whether persistent personality files will be used with [../03-reference/memory-and-personality.md](../03-reference/memory-and-personality.md).
5. Choose the Git usage pattern with [git-usage.md](git-usage.md).
6. Decide workspace isolation with [workspace-isolation.md](workspace-isolation.md).
7. Set directory responsibilities with [../03-reference/directory-conventions.md](../03-reference/directory-conventions.md).
8. Create the mission brief from `../templates/01-setup/MISSION_BRIEF_TEMPLATE.md`.
9. Create persistent behavior files from `../templates/01-setup/PERSONALITY_TEMPLATE.md` if your run uses them.
10. Start Commander with `../prompts/COMMANDER_THREAD_PROMPT.md`.
11. If the user needs direct steering access, create a visible Shoulder thread with `../prompts/SHOULDER_THREAD_PROMPT.md`.
12. Copy the live-run templates you need into the project workspace, not back into the kit itself.

## Minimum Files To Start A New Run

Read first:

- [reference-use-case.md](reference-use-case.md)
- [../03-reference/agent-topology.md](../03-reference/agent-topology.md)
- [../03-reference/coordination-primitives.md](../03-reference/coordination-primitives.md)
- [../03-reference/memory-and-personality.md](../03-reference/memory-and-personality.md)
- [git-usage.md](git-usage.md)
- `../prompts/COMMANDER_THREAD_PROMPT.md`
- [../02-runbook/README.md](../02-runbook/README.md)
- [../03-reference/directory-conventions.md](../03-reference/directory-conventions.md)
- [workspace-isolation.md](workspace-isolation.md)

Usually copy these into the new run:

- `../templates/01-setup/MISSION_BRIEF_TEMPLATE.md`
- `../templates/01-setup/PUBLIC_TRIAL_BRIEF_TEMPLATE.md` if the run is a comparative trial
- `../templates/01-setup/PERSONALITY_TEMPLATE.md` if persistent behavior files are part of the run
- `../templates/03-checkpoints/RUN_MONITOR_TEMPLATE.md`
- `../templates/02-dispatch/COMMAND_DISPATCH_TEMPLATE.md`
- `../templates/02-dispatch/SEND_READY_PROMPT_TEMPLATE.md`
- `../templates/03-checkpoints/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- `../templates/04-handoff/SUBMISSION_PACKET_TEMPLATE.md`
- `../templates/04-handoff/FINAL_HANDOFF_TEMPLATE.md`
- `../templates/04-handoff/KIT_RETROSPECTIVE_TEMPLATE.md`

Add these when the run needs them:

- `../templates/01-setup/00_INDEX_TEMPLATE.md`
- `../templates/03-checkpoints/INTERFACE_CONTRACT_FREEZE_TEMPLATE.md`
- `../templates/03-checkpoints/VERIFICATION_RECORD_TEMPLATE.md`
- `../templates/03-checkpoints/LANGUAGE_AND_ONBOARDING_CHECKLIST_TEMPLATE.md`
- `../templates/04-handoff/GAME_JUDGING_SCORECARD_TEMPLATE.md` for comparative browser-game trials

## Suggested Directory Layout In The Target Workspace

```text
your-project/
  assets/
    coordination-kit/
  run-ops/
  run-workspaces/
    arm-a/
    arm-b/
```

If this is specifically a comparative trial, `trial-ops/` and `trial-runs/` are also reasonable names.

If the kit stays external:

```text
coordination-kit/
your-project/
  run-ops/
  run-workspaces/
```

## Update Policy

- Treat the kit as reusable source material.
- Keep run-specific files outside the kit.
- If you improve the kit during a live run, capture the idea and publish the kit update after final review unless a safety issue forces immediate change.

## Before Publishing Or Reusing Widely

- Read [../04-maintainers/publishing-checklist.md](../04-maintainers/publishing-checklist.md).
- Add a license if the repository will be public.
- Make sure all relative references still make sense when `coordination-kit` is the repository root.

## Next Docs

- Generic topology: [../03-reference/agent-topology.md](../03-reference/agent-topology.md)
- Protocol, state, and policy: [../03-reference/coordination-primitives.md](../03-reference/coordination-primitives.md)
- Memory and personality: [../03-reference/memory-and-personality.md](../03-reference/memory-and-personality.md)
- Reference use case: [reference-use-case.md](reference-use-case.md)
- Git usage recommendation: [git-usage.md](git-usage.md)
- Live execution: [../02-runbook/README.md](../02-runbook/README.md)
- Preflight check: [../02-runbook/bootstrap-checklist.md](../02-runbook/bootstrap-checklist.md)
- Standalone release prep: [../04-maintainers/publishing-checklist.md](../04-maintainers/publishing-checklist.md)

## Japanese

`coordination-kit` を別 workspace に導入するときの日本語案内です。
このファイルでは英語本文のあとに日本語を続けて置いています。

コードの framework ではなく、visible multi-agent operations のための document と template 集です。package manager で install するものではありません。

### このキットが向いている場面

- 1 人の人間や上位 thread が、複数の agent lane を同時に監督したい
- prompt だけでは足りず、handoff、検証、統合のための visible file が欲しい
- プロジェクトごとに再利用できる coordination 資産を持ちたい

### protocol / state / policy の見方

この kit は次の 3 層で理解すると分かりやすいです。

- `protocol`: 誰が誰に何を dispatch し、どう acknowledge し、どう handoff するか
- `state`: どのファイルが現在の真実を持つか
- `policy`: 誰がどの decision authority を持つか

まとまった説明は [../03-reference/coordination-primitives.md](../03-reference/coordination-primitives.md) にあります。

### このキットが向いていない場面

- 1 agent と 1 user でそのまま終わる小タスク
- workflow engine や scheduler、runtime を探している場合
- visible file や explicit dispatch を運用するつもりがない場合

### 代表ユースケース

この repo の front-door 例は「まとまったソフトウェア変更を、実装 lane と検証 lane に分けて進める run」です。
詳しくは [reference-use-case.md#japanese](reference-use-case.md#japanese) を読むと、何に使うキットなのかが早く掴めます。

### このリポジトリの見方

- `../README.md`: リポジトリ全体の入口
- `../01-start-here/`: 導入と初期設定
- `../02-runbook/`: 実行中の運用ルール
- `../03-reference/`: 汎用トポロジ、memory モデル、固定ルール、振り返り知見
- `../04-maintainers/`: 公開や保守用の資料
- `../prompts/`: Commander と Shoulder を始動するときのプロンプト
- `../templates/`: 実運用にコピーして使うテンプレート群

### 最初に読む順番

1. [../README.md#japanese](../README.md#japanese)
2. [reference-use-case.md#japanese](reference-use-case.md#japanese)
3. [../03-reference/agent-topology.md](../03-reference/agent-topology.md)
4. [../03-reference/coordination-primitives.md](../03-reference/coordination-primitives.md)
5. [../03-reference/memory-and-personality.md](../03-reference/memory-and-personality.md)
6. [git-usage.md](git-usage.md)
7. [workspace-isolation.md](workspace-isolation.md)
8. [../02-runbook/README.md](../02-runbook/README.md)
9. [../03-reference/README.md](../03-reference/README.md)

### 10分で始める手順

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

### node 名の標準

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

### mode の扱い

`Explore / Verify / Integrate` は便利な代表例ですが、固定クラスではありません。

必要なら別の mode 名を使って構いません。大事なのは、いま何を重視している node なのかを明示することです。

### どのフォルダに何があるか

- `../templates/01-setup/`: 実行前に作る基本ファイル
- `../templates/02-dispatch/`: 誰に何を読ませて動かすかの指示系
- `../templates/03-checkpoints/`: 中間チェック、再配分、検証記録
- `../templates/04-handoff/`: 提出、評価、最終引き継ぎ

この分け方にしているので、「どの段階で使う書類か」がフォルダ名だけでも分かるはずです。

### どのファイルをいつ使うか

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

### 日本語運用で意識したい点

- reviewer 向けや end-user 向けの説明がある run では、同じ主言語でそろえる
- ルール説明は開始直後に見える場所へ置く
- demo checkpoint を置く run では、`midpoint playable` を「たぶん動く」ではなく「通しで見せられる」の意味で使う
- ファイルを書いただけでは指示にならないので、読む相手に明示的に送る
- 中盤以降は実装だけでなく、検証、文書化、ローカライズ、handoff にも担当を配る
- `PERSONALITY` と `WORKING_MEMORY` は混ぜない
- personality は自動学習させず、必要なら明示的に更新する

### 推奨ディレクトリ例

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

### 迷ったときの入口

- 新規導入: [../README.md#japanese](../README.md#japanese)
- 代表ユースケース: [reference-use-case.md#japanese](reference-use-case.md#japanese)
- 実運用: [Runbook](../02-runbook/README.md)
- 公開前確認: [Publishing Checklist](../04-maintainers/publishing-checklist.md)
