# Project Placement And Boundaries

Use this when deciding where `coordination-kit` should live and where the AI is allowed to write.

This is the main setup document for path rules, writable boundaries, and project layout.

English comes first in this file. A Japanese mirror appears later in the same document.

## Recommended Default

The safest default is:

```text
workspace/
  coordination-kit/
  your-project/
    run-ops/
    run-workspaces/
      arm-a/
      arm-b/
```

Read this layout like this:

- `workspace/` is only a container
- `coordination-kit/` is reusable source material and should stay mostly read-only
- `your-project/run-ops/` is for shared live coordination files
- `your-project/run-workspaces/arm-*/` is for lane-local writable work

## What To Tell The AI First

Always tell the AI two things before it starts:

1. the exact kit path
2. the exact writable project paths

Example:

```text
The reusable coordination kit is at ../coordination-kit.
Before creating anything, confirm that you can read ../coordination-kit and that you will write only under ./run-ops and ./run-workspaces.
Do not create live run files in ../ or inside ../coordination-kit.
Write only inside this project, mainly under ./run-ops and ./run-workspaces.
Use coordination-kit as the coordination method for this project.
```

If you do not name both the read path and the write path, the AI may search too broadly or place files in the wrong directory.
It is safer to make the AI repeat those boundaries back before it creates the first run file.

## Placement Options

### Option 1: Sibling Repository

Keep `coordination-kit` next to the project.

Use this when:

- you want the cleanest default
- the kit is mainly reusable guidance
- you want to update or replace the kit independently

### Option 2: Git Submodule

Put the kit inside the project only when the project must pin a specific kit revision.

```bash
git submodule add <repo-url> assets/coordination-kit
git submodule update --init --recursive
```

Use this when:

- the project needs a versioned in-repo reference
- the team is comfortable with submodule workflow
- the kit should stay mostly read-only during runs

### Option 3: Vendor Copy

Copy the files without the kit's `.git` history.

Use this when:

- you only need a local snapshot
- upstream sync is not important
- you want the least Git complexity

### Pattern To Avoid

Avoid a plain nested clone inside an already versioned project.

```text
your-project/
  .git/
  coordination-kit/
    .git/
```

Why to avoid it:

- parent Git commands can behave in surprising ways
- the nested repo may be staged as a gitlink instead of ordinary files
- collaborators may not receive the content you expected

## Writable Boundary Rules

- do not use `workspace/` itself as a live run area
- do not write live run files back into `coordination-kit/`
- keep shared live coordination files in `run-ops/`
- keep lane-local writable files in `run-workspaces/arm-*/`
- if a file is reusable policy, prompt text, or a template, keep it in the kit
- if a file belongs only to the active run, keep it in the project

## Directory Responsibilities

- `coordination-kit/` or `assets/coordination-kit/`
  - reusable prompts, templates, and stable policy
- `run-ops/`
  - mission, integration, run monitor, verification, handoff, and other shared run files
- `run-workspaces/arm-*/`
  - per-lane code, logs, working memory, local handoff, and other lane-local files

If the run is explicitly comparative, `trial-ops/` and `trial-runs/arm-*/` are also acceptable names.

## File Conventions Worth Keeping

For human-facing files that may create ambiguity, add:

```text
- Owner:
- Readers:
```

If a directory is likely to accumulate many files, create `00_INDEX.md` for navigation.

## Dispatch Rule

Writing a file is not the same thing as dispatching work.

If the AI or another node must read a file and act:

1. write or update the file
2. send an explicit message naming the file
3. state the required action
4. include the deadline when needed

## Human Language Rule

Choose one primary human language for the run and keep user-facing, reviewer-facing, or stakeholder-facing materials aligned to it.

## When To Introduce Git Worktrees

Use Git worktrees only if you need:

- branch history for each lane
- repeatable diffs between lane outputs
- isolation that follows Git branches rather than plain directories

Keep worktrees under the project root, for example:

```text
your-project/
  worktrees/
    arm-a/
    arm-b/
```

Do not create active worktrees above the current project root.

## Related Docs

- [Start Here](README.md)
- [Reference Use Case](reference-use-case.md)
- [Runbook](../02-runbook/README.md)
- [AI / System Reference](../03-reference/README.md)

## Japanese

`coordination-kit` をどこへ置くか、そして AI にどこまで書いてよいかを決めるための文書です。

path ルール、writable boundary、project layout の本体はこのファイルに集約しています。

## 推奨の基本形

いちばん安全な既定は次です。

```text
workspace/
  coordination-kit/
  your-project/
    run-ops/
    run-workspaces/
      arm-a/
      arm-b/
```

このレイアウトの意味:

- `workspace/` は container
- `coordination-kit/` は再利用する source material で、基本は read-only
- `your-project/run-ops/` は shared な live coordination file
- `your-project/run-workspaces/arm-*/` は lane ごとの writable work area

## 最初に AI へ伝えること

AI には、作業開始前に必ず次の 2 つを伝えます。

1. kit の実パス
2. project 側の書き込み先

例:

```text
再利用する coordination kit は ../coordination-kit にある。
何か作る前に、../coordination-kit を読めることと、書き込みが ./run-ops と ./run-workspaces に限定されることを確認する。
live run file を ../ や ../coordination-kit の中には作らない。
書き込みはこの project 配下、主に ./run-ops と ./run-workspaces に限定する。
この project では coordination-kit を coordination method として使う。
```

read path と write path の両方を明示しないと、AI が広く探索したり、誤った場所へ file を置いたりしやすくなります。
最初の run file を作る前に、その境界を AI に言い返させるとさらに安全です。

## 配置パターン

### Option 1: sibling repository

`coordination-kit` を project の横に置きます。

向いている場面:

- いちばん素直で安全な既定にしたい
- kit を再利用用の guidance として使いたい
- kit を project と独立して更新したい

### Option 2: Git submodule

project 側で kit revision を固定したいときだけ、project の中に入れます。

```bash
git submodule add <repo-url> assets/coordination-kit
git submodule update --init --recursive
```

向いている場面:

- 特定の kit revision を project が pin したい
- team が submodule workflow に慣れている
- run 中は kit をほぼ read-only reference として扱いたい

### Option 3: vendor copy

`.git` history なしで files だけコピーします。

向いている場面:

- local snapshot だけ欲しい
- upstream sync が重要ではない
- Git complexity を最小にしたい

### 避けたいパターン

すでに Git 管理されている project の中へ、plain な nested clone を置くのは避けてください。

```text
your-project/
  .git/
  coordination-kit/
    .git/
```

避ける理由:

- 親 repo の Git 挙動が分かりにくくなる
- nested repo が通常 file ではなく gitlink として stage されることがある
- collaborator に意図した中身が渡らないことがある

## 書き込み境界ルール

- `workspace/` 直下を live run area にしない
- `coordination-kit/` の中へ live run file を書かない
- shared な live coordination file は `run-ops/`
- lane ごとの writable file は `run-workspaces/arm-*/`
- reusable な policy、prompt、template は kit 側
- active run 固有の file は project 側

## ディレクトリ責務

- `coordination-kit/` または `assets/coordination-kit/`
  - 再利用する prompt、template、stable policy
- `run-ops/`
  - mission、integration、run monitor、verification、handoff など shared run file
- `run-workspaces/arm-*/`
  - lane ごとの code、log、working memory、local handoff など

比較型 run なら、`trial-ops/` や `trial-runs/arm-*/` でも構いません。

## あるとよい file の約束

曖昧になりそうな human-facing file には、次を付けると安全です。

```text
- Owner:
- Readers:
```

file が増えそうな directory には、navigation 用の `00_INDEX.md` を作ります。

## Dispatch Rule

file を書くだけでは dispatch になりません。

AI や別 node に読ませて動かしたいなら:

1. file を書くか更新する
2. file 名を明示して送る
3. 必要な action を書く
4. 必要なら deadline も書く

## 人間向け言語ルール

run の primary human language を 1 つ決めて、user-facing、reviewer-facing、stakeholder-facing の資料はその言語でそろえます。

## Git worktree を入れるタイミング

Git worktree は、次が必要になってからで十分です。

- lane ごとの branch history
- lane 間 diff の再現
- plain directory ではなく branch ベースの isolation

作るなら project root 配下に置きます。

```text
your-project/
  worktrees/
    arm-a/
    arm-b/
```

active worktree を project root の外に作らないでください。

## 関連ドキュメント

- [Start Here](README.md)
- [Reference Use Case](reference-use-case.md)
- [Runbook](../02-runbook/README.md)
- [AI / System Reference](../03-reference/README.md)
