# Coordination Kit

A documentation-first operating kit for visible, auditable multi-agent work.

Use this when one human or top-level coordinator needs to run several agent lanes on the same task without losing traceability, handoff quality, or integration ownership.

This repository is not a workflow engine, distributed runtime, or graph DSL. It gives you prompts, templates, and runbook rules for coordinating real work in visible files.

English comes first in this file. A Japanese mirror appears later in the same document.

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
  Arm B (Bravo team lane)
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

For read-aloud team names, many runs treat `A / B / C / D` as call-sign style Arm names such as `Alpha / Bravo / Charlie / Delta`.

The structure is intentionally stage-based: at every directory level, the first file to read is `README.md` in that directory.

## What This Is

- a reusable coordination layer for human-supervised multi-agent runs
- a visible-file operating model for prompts, handoff, verification, and sign-off
- a way to keep reusable policy separate from run-local writable state

## Canonical Example

The default front-door example is a scoped software delivery run:

- `Commander` owns the mission and final integration.
- `Arm A` is one implementation team lane.
- `Arm B` is one verification and handoff-support team lane.
- Lower nodes such as `A.Indy`, `A.Middy`, and `B.Thumb` execute concrete subtasks and report through visible files.

See [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md) for the concrete walk-through. The same file includes a Japanese section after the English section.

## Best Fits

- AI-assisted software delivery where one operator supervises multiple visible agent lanes
- multi-arm exploration or comparison runs where you need explicit handoff and integration
- human-in-the-loop workflows where prompts alone are not enough and auditability matters

Competitive browser-game trials are still supported, but they are now one profile, not the default concept.

## What This Is Not

- not a replacement for `Temporal`, `Airflow`, or other workflow schedulers
- not a compute runtime such as `Ray`
- not a graph execution framework such as `LangGraph`
- not the right tool for a tiny one-thread task with no handoff or verification pressure

## Start Here

- Bilingual onboarding: [01-start-here/README.md](01-start-here/README.md)
- Bilingual reference use case: [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md)
- Git usage recommendation: [01-start-here/git-usage.md](01-start-here/git-usage.md)
- Generic runbook: [02-runbook/README.md](02-runbook/README.md)
- Topology and naming: [03-reference/agent-topology.md](03-reference/agent-topology.md)
- Memory and personality: [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md)

## Read In Order

1. [01-start-here/README.md](01-start-here/README.md)
2. [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md)
3. [03-reference/agent-topology.md](03-reference/agent-topology.md)
4. [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md)
5. [02-runbook/README.md](02-runbook/README.md)
6. [prompts/README.md](prompts/README.md)
7. [templates/README.md](templates/README.md)
8. [04-maintainers/README.md](04-maintainers/README.md) if you maintain or publish the kit

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

## Recommended Use Order

1. Read [01-start-here/README.md](01-start-here/README.md).
2. Read the front-door example in [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md).
3. If Japanese guidance is needed, continue to the Japanese sections in those same files.
4. Choose the Git placement pattern with [01-start-here/git-usage.md](01-start-here/git-usage.md).
5. Fix the generic topology with [03-reference/agent-topology.md](03-reference/agent-topology.md).
6. Confirm memory separation with [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md).
7. Choose workspace isolation with [01-start-here/workspace-isolation.md](01-start-here/workspace-isolation.md).
8. Operate the run with [02-runbook/README.md](02-runbook/README.md).
9. Copy prompts and templates from [prompts/README.md](prompts/README.md) and [templates/README.md](templates/README.md) into your run workspace.
10. Review [03-reference/lessons-learned.md](03-reference/lessons-learned.md) after each run and update the kit after final review is complete.

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

`coordination-kit` は、見える multi-agent 運用のための documentation-first operating kit です。

1 人の人間または上位 coordinator が、同じ task に対して複数の agent lane を走らせたいときに使います。
runtime や workflow engine ではなく、prompt、template、runbook rule を visible file ベースで組み立てるためのキットです。

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
  Arm B (Bravo team lane)
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

会話上は `A / B / C / D` を、`Alpha / Bravo / Charlie / Delta` のような team callsign として読むとイメージしやすいです。

### このキットが何か

- human-supervised multi-agent run のための再利用可能な coordination layer
- handoff、verification、sign-off を visible file で回す operating model
- 再利用する policy と run ごとの writable state を分けるための構成

### 代表ユースケース

入口の標準例は、スコープを絞ったソフトウェア変更です。

- `Commander` が mission と最終統合を持つ
- `Arm A` が実装チーム lane として動く
- `Arm B` が検証と docs / handoff 支援のチーム lane として動く
- `A.Indy` や `B.Thumb` のような lower node が visible file 経由で具体タスクを進める

詳しくは [01-start-here/reference-use-case.md](01-start-here/reference-use-case.md) を見てください。
同じファイルの後半に日本語の代表例があります。

### 向いている場面

- 1 人の operator が複数の visible agent lane を監督する AI-assisted software delivery
- 明示的な handoff と integration が必要な multi-arm exploration や comparison run
- prompt だけでは足りず、auditability が必要な human-in-the-loop workflow

browser-game の competitive trial も扱えますが、それは optional profile です。標準の前提ではありません。

### 向いていない場面

- `Temporal` や `Airflow` のような workflow scheduler の代わり
- `Ray` のような compute runtime
- `LangGraph` のような graph execution framework
- handoff や verification が不要な小さな 1-thread task

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
