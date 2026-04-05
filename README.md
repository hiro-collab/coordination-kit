# Coordination Kit

If you are thinking, "I want AI to work in parallel, but how should I structure the coordination first?", start here.

A documentation-first operating kit for visible, auditable multi-agent work.

Use this when one human or top-level coordinator needs to run several agent lanes on the same task without losing traceability, handoff quality, or integration ownership.

This repository is not a workflow engine, distributed runtime, or graph DSL. It gives you prompts, templates, and runbook rules for coordinating real work in visible files.

English comes first in this file. A Japanese mirror appears later in the same document.

In one paragraph: `coordination-kit` is a visible operating model for multi-team human and AI work. A `Commander` owns overall direction and final responsibility, while one or more Arms such as `Alpha`, `Blabo`, `Charlie`, and `Delta` run in parallel as team identities. Inside each Arm, `Shoulder`, optional `Elbow`, and `Fingers` carry the current work. The important point is that Arm names are not job titles. They are stable team IDs, while implementation, verification, research, or handoff duties are assigned per run.

## How To Use First

Put `coordination-kit` next to your project as a sibling directory.
That is the safest default.

```text
workspace/
  coordination-kit/
  your-project/
    run-ops/
    run-workspaces/
```

Open the AI from `your-project/`, not from the shared `workspace/` parent.

Then open both directories in a file-aware AI coding system such as Codex or Claude Code, and say something like:

```text
The reusable coordination kit is at ../coordination-kit.
Before creating anything, confirm that you can read ../coordination-kit and that you will write only under ./run-ops and ./run-workspaces.
Do not write live run files in ../ or inside ../coordination-kit.
Write only inside this project, mainly under ./run-ops and ./run-workspaces.
Use coordination-kit as the coordination method for this project.
You are Commander.
Create Arm A and Arm B as team lanes.
Start as Commander first.
When lane-level direct steering is needed, use `A.Shoulder` and `B.Shoulder` as the first acting threads inside those lanes.
Create `MISSION_BRIEF.md`, `SHARED_NOTE.md`, and `INTEGRATION.md` first, then create node-local working-memory or log files, plus `VERIFICATION_RECORD.md` or `FINAL_HANDOFF.md` when needed.
Keep ownership explicit and do not sign off until the final integration is complete.
```

What you get:

- parallel AI lanes without losing ownership
- visible handoff and verification instead of hidden context
- one clear place for integration and final sign-off
- easier mid-run rebalancing when one lane stalls or drifts

Your first visible outputs should usually be:

- `MISSION_BRIEF.md` for scope and finish conditions
- `SHARED_NOTE.md` for shared interfaces, file ownership, and active assumptions
- `INTEGRATION.md` as the shared integration file
- one or more `WORKING_MEMORY.<node>.md` or `LOG.<node>.md` files for active lanes
- `VERIFICATION_RECORD.md` or `FINAL_HANDOFF.md` before sign-off

Boundary rule:

- `workspace/` is only a container, not a live working area
- `coordination-kit/` is reusable source material and should stay mostly read-only
- normal live writes belong in `your-project/run-ops/` and `your-project/run-workspaces/`

If the kit must live inside the project repository, use a Git submodule instead of a plain nested clone.

If you are the human operator, you can usually stop after this `README.md`, [01-start-here/README.md](01-start-here/README.md), and [02-runbook/README.md](02-runbook/README.md). Open `03-reference/`, `prompts/`, and `templates/` only when you need deeper rules or reusable assets.

The default concept is generic:

- Commander coordinates across one or more Arms.
- Each Arm is a parallel team lane under Commander.
- Inside each Arm, the usual structure is Shoulder -> optional Elbow -> Fingers.
- Node names are identifiers, not fixed roles.

If an Arm uses five finger lanes, the standard local names are `Thumb`, `Indy`, `Middy`, `Ringy`, and `Pinky`. Use compact node IDs such as `A.Thumb`, `A.Middy`, and `B.Shoulder`.

## Hierarchy At A Glance

This is a nested structure, not a flat list of unrelated parts.

```text
Commander
  Arm A (Alpha team lane)
    A.Shoulder
      A.Elbow (optional)
        A.Thumb
        A.Indy
        A.Middy
        A.Ringy
        A.Pinky
  Arm B (Blabo team lane)
    B.Shoulder
      B.Thumb
      B.Indy
      ...
```

Read it like this:

- `Commander` is the top-level coordinator.
- `Arm` means one parallel team lane under Commander.
- The visible acting threads are usually `Commander` and one or more `Shoulder` nodes.
- `Shoulder`, `Elbow`, and `Fingers` belong inside one specific Arm.
- An `Arm` is usually the lane or container name, not a separate acting thread by itself.
- `Elbow` is optional. Shoulder may control Fingers directly.
- Fingers are never a shared global pool. `A.Thumb` belongs to Arm A, `B.Thumb` belongs to Arm B.

For read-aloud team names, many runs treat `A / B / C / D` as call-sign style Arm names such as `Alpha / Blabo / Charlie / Delta`. `Blabo` is intentional in this kit; use another stable call-sign if your team prefers.

The structure is intentionally stage-based: at every directory level, the first file to read is `README.md` in that directory.

## What This Is

- a reusable coordination layer for human-supervised multi-agent runs
- a visible-file operating model for prompts, handoff, verification, and sign-off
- a protocol/state/policy model for explicit multi-lane coordination
- a way to keep reusable policy separate from run-local writable state

## Canonical Example

The default front-door example is a scoped software delivery run.

Typical user intent:

- "Add a feature, keep the API stable, and let AI work in parallel."

Typical first result:

- one lane starts implementation-heavy work
- another lane starts verification, docs, or handoff-heavy work
- the user can still see who owns scope, what is blocked, and who may sign off

See [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md) for the concrete walk-through. The same file includes a Japanese section after the English section.

## Best Fits

- AI-assisted software delivery where one operator supervises multiple visible agent lanes
- multi-arm exploration or comparison runs where you need explicit handoff and integration
- human-in-the-loop workflows where prompts alone are not enough and auditability matters

Competitive browser-game trials are still supported, but they are now one profile, not the default concept.

## What This Is Not

- not an execution engine that runs jobs, retries, or background workflows for you
- not a distributed compute runtime that spreads code across machines
- not an agent-graph runtime that executes a graph for you
- not the right tool for a tiny one-thread task with no handoff or verification pressure

### Nearby Tools At Other Layers

If you know these tools, the rough comparison is:

- `Temporal` or `Airflow`: workflow schedulers that run and track background flows
- `Ray`: a distributed compute runtime for parallel execution
- `LangGraph`: a graph-shaped runtime for agent flows
- `coordination-kit`: a visible coordination layer for humans and agents working across multiple lanes

So yes, similar tools exist nearby, but they solve a different layer of the problem. This kit is about structure, visibility, handoff, and responsibility, not job execution.

## Open Next

- Human operator next step: [01-start-here/README.md](01-start-here/README.md)
- Placement and write-boundary rules: [01-start-here/project-placement.md](01-start-here/project-placement.md)
- Live operation runbook: [02-runbook/README.md](02-runbook/README.md)
- Concrete example when needed: [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md)
- AI / system rules only when needed: [03-reference/README.md](03-reference/README.md)
- Prompt assets only when starting visible AI threads: [prompts/README.md](prompts/README.md)
- Template assets only when creating live run files: [templates/README.md](templates/README.md)
- Maintainer docs: [04-maintainers/README.md](04-maintainers/README.md)

## Repository Structure

```text
coordination-kit/
  01-start-here/
  02-runbook/
  03-reference/
  04-maintainers/
  prompts/
  templates/
  CHANGELOG.md
  LICENSE
  README.md
```

- `01-start-here/` is for user-facing adoption and project setup.
- `02-runbook/` is for live execution.
- `03-reference/` holds AI / system rules such as topology, protocol, memory, and lessons learned.
- `04-maintainers/` is for release and publishing work.
- `prompts/` contains startup prompts for Commander and active Shoulder threads.
- `templates/` contains reusable coordination files grouped by run phase.

## Core Rules

- Higher-level nodes decompose and integrate; lower-level nodes execute.
- Roles are not fixed by Arm or Finger name.
- Keep reusable kit files separate from run-specific writable files.
- Treat file creation as storage, not instruction delivery.
- Keep persistent personality separate from task-specific working memory.
- Do not auto-update personality from working memory.
- Use visible artifacts for handoff, verification, and sign-off.
- Keep human-facing materials aligned to the run's primary human language.
- After midpoint or the first integrated build, redistribute work visibly instead of letting everything collapse back to one operator.
- Use compact node IDs when lower nodes are active, for example `A.Thumb`, `A.Indy`, `A.Middy`, `A.Ringy`, and `A.Pinky`.

## Standalone Repository Notes

If you publish this kit as its own repository:

1. Keep this directory as the repository root.
2. Keep run-specific artifacts outside this repository.
3. Review [04-maintainers/publishing-checklist.md](04-maintainers/publishing-checklist.md) before release.

## Japanese

「AI に並列処理をやらせたいけど、とりあえず連携の組み方をどうしよう」と思ったら、ここから読むのが入口です。

`coordination-kit` は、見える multi-agent 運用のための documentation-first operating kit です。

1 人の人間または上位 coordinator が、同じ task に対して複数の agent lane を走らせたいときに使います。
runtime や workflow engine ではなく、prompt、template、runbook rule を visible file ベースで組み立てるためのキットです。

短く言うと、`coordination-kit` は複数の human / AI チームを見える形で運用するための型です。`Commander` が全体方針と最終責任を持ち、`Alpha`、`Blabo`、`Charlie`、`Delta` のような Arm が並列に動きます。各 Arm の内部では `Shoulder`、必要なら `Elbow`、`Fingers` が仕事を回します。大事なのは、Arm 名は担当名ではないことです。Arm は安定した team ID であり、実装、検証、調査、handoff などの担当は run ごとの assign で変わります。

### 最初の使い方

まず `coordination-kit` を project の横に sibling directory として置きます。
これがいちばん安全な既定です。

```text
workspace/
  coordination-kit/
  your-project/
    run-ops/
    run-workspaces/
```

AI は shared な `workspace/` 親ではなく、`your-project/` を起点に開いてください。

そのうえで、Codex や Claude Code のような file-aware AI coding system に、たとえば次のように伝えます。

```text
再利用する coordination kit は ../coordination-kit にある。
何か作る前に、../coordination-kit を読めることと、書き込みが ./run-ops と ./run-workspaces に限定されることを確認する。
live run file を ../ や ../coordination-kit の中には作らない。
書き込みはこの project 配下、主に ./run-ops と ./run-workspaces に限定する。
この project では coordination-kit を coordination method として使う。
あなたは Commander として動く。
Arm A と Arm B を team lane として立てる。
まず Commander として始める。
lane ごとの direct steering が必要になったら、その最初の acting thread は `A.Shoulder` と `B.Shoulder` にする。
まず `MISSION_BRIEF.md`、`SHARED_NOTE.md`、`INTEGRATION.md` を作り、そのあと node ごとの working-memory か log、必要なら `VERIFICATION_RECORD.md` か `FINAL_HANDOFF.md` を用意する。
ownership を明示し、最終統合が終わるまで sign-off しない。
```

この kit を使うと、次の利点があります。

- AI を並列で動かしても ownership が崩れにくい
- handoff や verification が hidden context ではなく visible file になる
- integration と final sign-off の責任者が明確になる
- 途中で lane が詰まっても再配分しやすい

最初の導入が正しくできているなら、たいてい最初に次の visible file が見えるはずです。

- scope と finish condition を書いた `MISSION_BRIEF.md`
- shared interface、file ownership、active assumption をまとめる `SHARED_NOTE.md`
- shared integration file である `INTEGRATION.md`
- 動いている lane ごとの `WORKING_MEMORY.<node>.md` か `LOG.<node>.md`
- sign-off 前に確認する `VERIFICATION_RECORD.md` か `FINAL_HANDOFF.md`

境界ルール:

- `workspace/` 直下は container であって live working area ではない
- `coordination-kit/` は再利用する source material で、基本は read-only
- 通常の live file は `your-project/run-ops/` と `your-project/run-workspaces/` に置く

もし kit を project repository の中に置く必要があるなら、plain な nested clone ではなく Git submodule を使うのが安全です。

人間の operator なら、通常はこの `README.md` と [01-start-here/README.md](01-start-here/README.md)、[02-runbook/README.md](02-runbook/README.md) までで十分です。`03-reference/`、`prompts/`、`templates/` は、固定ルールや再利用 asset が必要になってから開けば構いません。

### 階層の見え方

これは `Commander -> Arms -> Shoulder / Elbow / Fingers` という平らな並びではなく、Arm の中に下位構造が入る入れ子です。

```text
Commander
  Arm A (Alpha team lane)
    A.Shoulder
      A.Elbow (optional)
        A.Thumb
        A.Indy
        A.Middy
        A.Ringy
        A.Pinky
  Arm B (Blabo team lane)
    B.Shoulder
      B.Thumb
      B.Indy
      ...
```

つまり:

- `Commander` が最上位
- `Arm` は Commander 配下の並列 team lane
- 実際に visible thread になりやすいのは `Commander` と各 Arm の `Shoulder`
- `Shoulder`、`Elbow`、`Fingers` はその Arm の内部構造
- `Elbow` は任意で、なくてもよい
- `A.Thumb` と `B.Thumb` は別の Arm に属する別 node

会話上は `A / B / C / D` を、`Alpha / Blabo / Charlie / Delta` のような team callsign として読むとイメージしやすいです。

### このキットが何か

- human-supervised multi-agent run のための再利用可能な coordination layer
- handoff、verification、sign-off を visible file で回す operating model
- 再利用する policy と run ごとの writable state を分けるための構成

### 代表ユースケース

入口の標準例は、スコープを絞ったソフトウェア変更です。

ユーザーの典型的な意図:

- 「機能追加はしたいが、API は壊したくない」
- 「AI を並列で動かしたいが、最後の責任は 1 か所に残したい」

最初に起きることの典型:

- ある lane で実装寄りの作業が進む
- 別の lane で検証、docs、handoff 寄りの作業が進む
- ユーザーは scope、blocker、sign-off 権限を visible file で追える

詳しくは [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md) を見てください。
同じファイルの後半に日本語の代表例があります。

### protocol / state / policy

この kit は、単なるフォルダ整理ではなく、次の 3 層で読むと分かりやすいです。

- `protocol`: 誰が誰に何を依頼し、どう acknowledge し、どう handoff するか
- `state`: 何が現在の真実で、どのファイルに保存されるか
- `policy`: 誰が何を決める authority を持つか

まとまった説明は [03-reference/coordination-primitives.md](03-reference/coordination-primitives.md) に置いてあります。

### 向いている場面

- 1 人の operator が複数の visible agent lane を監督する AI-assisted software delivery
- 明示的な handoff と integration が必要な multi-arm exploration や comparison run
- prompt だけでは足りず、auditability が必要な human-in-the-loop workflow

browser-game の competitive trial も扱えますが、それは optional profile です。標準の前提ではありません。

### 向いていない場面

- job 実行、retry、background workflow 実行そのものを任せたい場合
- 分散 compute runtime としてコードを複数 machine に投げたい場合
- agent graph をそのまま実行する runtime を探している場合
- handoff や verification が不要な小さな 1-thread task

### 近いレイヤーのツール

近い領域には、たとえば次のようなツールがあります。

- `Temporal` や `Airflow`: background workflow を実行して追跡する workflow scheduler
- `Ray`: 並列実行や分散実行のための compute runtime
- `LangGraph`: graph 形状の agent flow を動かす runtime
- `coordination-kit`: human と agent が複数 lane で動くときの visible coordination layer

つまり、近い問題を扱うツールはありますが、この kit が担当するのは job 実行ではなく、構造、可視化、handoff、責任分担です。

### 次に開くもの

- human operator の次の 1 枚: [01-start-here/README.md](01-start-here/README.md)
- 配置と書き込み境界: [01-start-here/project-placement.md](01-start-here/project-placement.md)
- live operation の runbook: [02-runbook/README.md](02-runbook/README.md)
- 具体例が欲しいとき: [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md)
- AI / system rule が必要になったときだけ: [03-reference/README.md](03-reference/README.md)
- visible AI thread を立てるときだけ: [prompts/README.md](prompts/README.md)
- live run file を作るときだけ: [templates/README.md](templates/README.md)

### コアルール

- 上位 node が分解と統合を持ち、下位 node が実行する
- Arm 名や Finger 名で役割を固定しない
- reusable kit file と run-specific writable file を分ける
- `PERSONALITY` と `WORKING_MEMORY` を分ける
- visible artifact を handoff、verification、sign-off の基準にする
