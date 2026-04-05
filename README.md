# Coordination Kit

If you are thinking, "I want AI to work in parallel, but how should I structure the coordination first?", start here.

A documentation-first operating kit for visible, auditable multi-agent work.

Use this when one human or top-level coordinator needs to run several agent lanes on the same task without losing traceability, handoff quality, or integration ownership.

This repository is not a workflow engine, distributed runtime, or graph DSL. It gives you prompts, templates, and runbook rules for coordinating real work in visible files.

English comes first in this file. A Japanese mirror appears later in the same document.

In one paragraph: `coordination-kit` is a visible operating model for multi-team human and AI work. A `Commander` owns overall direction and final responsibility, while one or more Arms such as `Alpha`, `Blabo`, `Charlie`, and `Delta` run in parallel as team identities. Inside each Arm, `Shoulder`, optional `Elbow`, and `Fingers` carry the current work. The important point is that Arm names are not job titles. They are stable team IDs, while implementation, verification, research, or handoff duties are assigned per run.

## How To Use First

Use the kit like this:

1. Name one `Commander` and one or more `Arm` team lanes.
2. Give `Commander` the mission, scope boundary, and final sign-off responsibility.
3. Inside each Arm, appoint a `Shoulder`. Add an `Elbow` only when that Arm needs another coordination layer.
4. Dispatch concrete work to lower nodes through visible files. A file by itself is storage, not instruction.
5. Keep stable behavior policy in `PERSONALITY`, run-local facts in `WORKING_MEMORY`, and shared run truth in mission, integration, verification, and handoff files.
6. Let `Shoulder` coordinate inside one Arm, let `Commander` rebalance across Arms, and let `Commander` own the final integration and sign-off.

If you cannot explain your run in these six steps, the run is still underspecified.

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
- `Shoulder`, `Elbow`, and `Fingers` belong inside one specific Arm.
- `Elbow` is optional. Shoulder may control Fingers directly.
- Fingers are never a shared global pool. `A.Thumb` belongs to Arm A, `B.Thumb` belongs to Arm B.

For read-aloud team names, many runs treat `A / B / C / D` as call-sign style Arm names such as `Alpha / Blabo / Charlie / Delta`.

The structure is intentionally stage-based: at every directory level, the first file to read is `README.md` in that directory.

## What This Is

- a reusable coordination layer for human-supervised multi-agent runs
- a visible-file operating model for prompts, handoff, verification, and sign-off
- a protocol/state/policy model for explicit multi-lane coordination
- a way to keep reusable policy separate from run-local writable state

## Canonical Example

The default front-door example is a scoped software delivery run:

- `Commander` owns the mission and final integration.
- `Arm A` and `Arm B` are stable team lanes, not fixed departments.
- In this example, current assignments place more implementation work in `Arm A` and more verification or handoff work in `Arm B`.
- Lower nodes such as `A.Indy`, `A.Middy`, and `B.Thumb` execute concrete subtasks and report through visible files.

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

## Reference Map

- Onboarding: [01-start-here/README.md](01-start-here/README.md)
- Concrete use case: [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md)
- Git placement guidance: [01-start-here/git-usage.md](01-start-here/git-usage.md)
- Workspace layout: [01-start-here/workspace-isolation.md](01-start-here/workspace-isolation.md)
- Live operation runbook: [02-runbook/README.md](02-runbook/README.md)
- Topology and naming: [03-reference/agent-topology.md](03-reference/agent-topology.md)
- Protocol, state, and policy: [03-reference/coordination-primitives.md](03-reference/coordination-primitives.md)
- Memory and personality: [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md)
- Lessons learned: [03-reference/lessons-learned.md](03-reference/lessons-learned.md)
- Prompt assets: [prompts/README.md](prompts/README.md)
- Template assets: [templates/README.md](templates/README.md)
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

- `01-start-here/` is for first-time adoption and workspace setup.
- `02-runbook/` is for live execution.
- `03-reference/` holds the generic topology, memory model, stable rules, and lessons learned.
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

この kit は、次の 6 ステップで使います。

1. まず `Commander` を 1 人決め、必要な数だけ `Arm` という team lane を置く
2. `Commander` に mission、scope boundary、最終 sign-off responsibility を持たせる
3. 各 Arm の中に `Shoulder` を置き、もう 1 段の調整役が必要なときだけ `Elbow` を置く
4. 下位 node には visible file 経由で具体タスクを dispatch する。ファイルを置いただけでは instruction にならない
5. 安定した振る舞い policy は `PERSONALITY`、run ごとの事実は `WORKING_MEMORY`、shared truth は mission、integration、verification、handoff file に分ける
6. Arm 内の調整は `Shoulder`、Arm 間の再配分と最終統合は `Commander` が持つ

この 6 ステップで説明しきれない run は、まだ設計が曖昧です。

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

- `Commander` が mission と最終統合を持つ
- `Arm A` と `Arm B` は担当固定ではなく、安定したチーム lane 名として動く
- この例では、その時点の assign として `Arm A` に実装寄りの作業が多く、`Arm B` に検証や docs / handoff 支援が多い
- `A.Indy` や `B.Thumb` のような lower node が visible file 経由で具体タスクを進める

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

### 最初に読む順番

1. [01-start-here/README.md](01-start-here/README.md)
2. [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md)
3. [03-reference/agent-topology.md](03-reference/agent-topology.md)
4. [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md)
5. [02-runbook/README.md](02-runbook/README.md)

### コアルール

- 上位 node が分解と統合を持ち、下位 node が実行する
- Arm 名や Finger 名で役割を固定しない
- reusable kit file と run-specific writable file を分ける
- `PERSONALITY` と `WORKING_MEMORY` を分ける
- visible artifact を handoff、verification、sign-off の基準にする
