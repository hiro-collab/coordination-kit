# Agent Topology

Use this as the generic concept document for the kit.

For a user, this file answers one question: "If I ask AI to work in parallel, what stable lane structure am I asking it to create?"

Use this before deeper operating rules. If the lane shape itself is still unclear, read this before `coordination-primitives.md`.

English comes first in this file. A Japanese mirror appears later in the same document.

Default starting point:

- one `Commander`
- one or two `Arm` lanes
- one `Shoulder` inside each active Arm
- `Elbow` only when one Arm needs another coordination layer
- `Fingers` only for concrete parallel tasks

If you cannot explain why a second Arm exists, you probably do not need it yet.

## Purpose

This project uses a hierarchical multi-agent coordination model.

The structure is inspired by a body metaphor:
higher-level coordinators steer lower execution nodes inside a stable lane structure.

This is a coordination model, not a literal anatomy.

## Topology

- Commander: top-level coordinator
- Arms: parallel lane IDs such as `A`, `B`, `C`, `D`
- Each Arm may contain:
  - Shoulder: direction and control
  - Elbow: optional decomposition layer
  - Fingers: execution slots

## Hierarchy Shape

Do not read this as a flat sequence like `Commander -> Arms -> Shoulder -> Elbow -> Fingers`.

The intended shape is:

```text
Commander
  Arm A
    Shoulder
      Elbow (optional)
        Thumb / Indy / Middy / Ringy / Pinky
  Arm B
    Shoulder
      Fingers...
```

This means:

- Commander owns the overall mission.
- Each Arm is one parallel team lane under Commander.
- Shoulder, Elbow, and Fingers belong inside a specific Arm.
- Elbow is optional, and Shoulder may directly control Fingers.
- `A.Thumb` and `B.Thumb` are different nodes because they belong to different Arms.

You can think of Arms as team units or squad lanes under a single Commander.

## Actor Model

- `Commander` is usually one visible top-level thread.
- `Shoulder` is the default acting thread inside an Arm.
- `Elbow` and `Fingers` become acting threads only when the run needs them.
- An `Arm` is usually the lane or container name, not a standalone actor thread by default.

## Core Principles

### Roles Are Not Fixed

- Arms do not have fixed roles.
- Fingers do not have fixed roles.
- Any node may perform research, implementation, validation, integration, or other work.

Structure is fixed. Meaning is dynamic.

### Delegation Model

Higher-level coordinators such as `Commander`, and within one Arm `Shoulder` or `Elbow` when active:

- decompose tasks
- assign work
- integrate results

Lower-level executors such as `Fingers`, and any node currently assigned execution-only work:

- execute assigned tasks
- avoid global decisions unless instructed

In user terms:

- `Arm` is the lane identity.
- lower acting nodes such as `Shoulder`, optional `Elbow`, and `Fingers` do the visible execution work inside that lane.

### Parallel Execution

- Decompose work into independent subtasks when possible.
- Assign subtasks across Arms or Fingers.
- Run in parallel when it reduces coordination cost or time risk.
- Merge results explicitly after execution.

### Hierarchical Communication

Preferred flow:

- Commander ⇄ Shoulder
- Shoulder ⇄ Elbow when Elbow exists
- Elbow or Shoulder ⇄ Fingers

Avoid unnecessary lateral communication.

## Naming Conventions

Arms:

- `A`, `B`, `C`, `D`

For read-aloud names, many runs treat these as call-sign style team names such as:

- `A` -> `Alpha`
- `B` -> `Blabo`
- `C` -> `Charlie`
- `D` -> `Delta`

`Blabo` is intentional in this kit as a distinct call-sign example. Replace it if your team prefers another stable name.

Project-specific team names are also acceptable as long as the compact IDs stay stable in files.

Finger local names:

- `Thumb`
- `Indy`
- `Middy`
- `Ringy`
- `Pinky`

Names are identifiers, not roles.

## Identification Format

Compact identifiers:

- `A.Thumb`
- `A.Middy`
- `B.Shoulder`
- `C.Elbow`

Human-readable examples:

- `Arm A Shoulder reports`
- `Message from Arm B Thumb`

## Structural Flexibility

- Some Arms may not have Elbow.
- Some Arms may have multiple Elbows.
- Shoulder may directly control Fingers.
- Finger count is often 5, but it may vary.

Common simplified shape without Elbow:

```text
Commander
  Arm A
    Shoulder
      Thumb / Indy / Middy / Ringy / Pinky
```

## Execution Model

Typical flow:

1. Commander receives task.
2. Commander assigns work to one or more Arms.
3. Shoulder defines direction.
4. Elbow, if present, decomposes further.
5. Fingers execute subtasks in parallel.
6. An upper layer integrates results.
7. Commander produces final output.

## Status Reporting

Always include node identity.

Examples:

- `[A.Shoulder] received task`
- `[A.Middy] processing`
- `[A.Ringy] validation complete`
- `[A.Thumb] consolidating results`
- `[Commander] final output ready`

## Completion Criteria

A task is complete only when:

- output is produced
- results are consistent
- assumptions are stated
- unresolved issues are listed

## Key Rule

Higher-level nodes decompose tasks, use lower-level nodes as parallel execution units, and integrate the results.

## Reading Map

- Read [coordination-primitives.md](coordination-primitives.md) next for protocol, state, and authority.
- Read [profile-inheritance/README.md](profile-inheritance/README.md) when the question shifts from structure to durable behavior.
- Read [lessons-learned.md](lessons-learned.md) only after the core model is already clear.

## Japanese

このファイルは、この kit における汎用的な topology の基準文書です。

利用者の言葉で言えば、このファイルが答える問いは 1 つです。
「AI に並列で仕事をさせるとき、どんな安定した lane 構造を作らせる前提なのか」

より深い運用ルールに入る前に、このファイルを読みます。lane の形そのものがまだ曖昧なら、`coordination-primitives.md` より先にここを読んでください。

既定の出発点:

- `Commander` は 1 つ
- `Arm` lane は 1 本か 2 本
- active な各 Arm の中に `Shoulder` を 1 つ
- `Elbow` は、ある Arm にもう 1 層の調整が必要なときだけ置く
- `Fingers` は、具体的な並列 task があるときだけ使う

2 本目の Arm がなぜ必要かを説明できないなら、まだ不要なことが多いです。

## 目的

この project では、階層型の multi-agent coordination model を使います。

構造は身体メタファーに着想を得ています。
上位の coordinator が、安定した lane 構造の中で下位の execution node を steer します。

これは coordination model であり、文字通りの身体構造ではありません。

## Topology

- `Commander`: 最上位の coordinator
- `Arms`: `A`, `B`, `C`, `D` のような並列 lane ID
- 各 Arm には必要に応じて次を含められる
  - `Shoulder`: 方向づけと制御
  - `Elbow`: 任意の追加分解 layer
  - `Fingers`: 実行 slot

## 階層の形

`Commander -> Arms -> Shoulder -> Elbow -> Fingers` のような平らな一直線として読まないでください。

意図している形は次です。

```text
Commander
  Arm A
    Shoulder
      Elbow (optional)
        Thumb / Indy / Middy / Ringy / Pinky
  Arm B
    Shoulder
      Fingers...
```

つまり:

- `Commander` が全体 mission を持つ
- 各 `Arm` は `Commander` 配下の 1 本の並列 team lane
- `Shoulder`、`Elbow`、`Fingers` は特定の Arm の内部に属する
- `Elbow` は任意で、`Shoulder` が直接 `Fingers` を制御してもよい
- `A.Thumb` と `B.Thumb` は別 Arm に属する別 node

`Arm` は、1 人の `Commander` 配下にある team unit や squad lane と考えると分かりやすいです。

## Actor Model

- `Commander` は通常 1 本の visible な top-level thread
- `Shoulder` は Arm 内の既定の acting thread
- `Elbow` と `Fingers` は、run で必要になったときだけ acting thread になる
- `Arm` は通常 standalone な actor thread ではなく、lane または container 名として使う

## Core Principles

### 役割は固定しない

- `Arms` に固定役割はない
- `Fingers` に固定役割はない
- どの node でも、research、implementation、validation、integration などを担当しうる

構造は固定、意味は動的です。

### Delegation Model

`Commander`、そして 1 つの Arm の中で active な `Shoulder` や `Elbow` のような上位 coordinator は:

- task を分解する
- work を割り当てる
- result を統合する

`Fingers` や execution-only に割り当てられている node のような下位 executor は:

- 割り当てられた task を実行する
- 指示なしに global decision を引き取らない

利用者の言葉で言えば:

- `Arm` は lane identity
- `Shoulder`、必要なら `Elbow`、`Fingers` のような下位 acting node が、その lane の visible な execution work を行う

### Parallel Execution

- 可能なら work を独立した subtasks に分解する
- subtasks を `Arms` や `Fingers` に割り当てる
- coordination cost や time risk が下がるなら並列に走らせる
- 実行後は result を明示的に merge する

### Hierarchical Communication

推奨フロー:

- `Commander` ⇄ `Shoulder`
- `Shoulder` ⇄ `Elbow` (`Elbow` があるとき)
- `Elbow` または `Shoulder` ⇄ `Fingers`

不要な横連携は避けます。

## Naming Conventions

Arms:

- `A`, `B`, `C`, `D`

読み上げ用の名前として、次のような call-sign style の team 名を使うことが多いです。

- `A` -> `Alpha`
- `B` -> `Blabo`
- `C` -> `Charlie`
- `D` -> `Delta`

`Blabo` は、この kit で distinct な call-sign の例として意図的に使っています。team に別の安定した名前があれば置き換えて構いません。

project 固有の team 名でも、compact ID が file 上で安定していれば問題ありません。

Finger のローカル名:

- `Thumb`
- `Indy`
- `Middy`
- `Ringy`
- `Pinky`

名前は identifier であり、役割ではありません。

## 識別子の形式

Compact identifier:

- `A.Thumb`
- `A.Middy`
- `B.Shoulder`
- `C.Elbow`

人間向けの読みやすい例:

- `Arm A Shoulder reports`
- `Message from Arm B Thumb`

## 構造の柔軟性

- `Elbow` を持たない Arm があってよい
- 複数の `Elbows` を持つ Arm があってよい
- `Shoulder` が直接 `Fingers` を制御してよい
- Finger 数は 5 が多いが、固定ではない

`Elbow` なしの簡略形は次です。

```text
Commander
  Arm A
    Shoulder
      Thumb / Indy / Middy / Ringy / Pinky
```

## Execution Model

典型的な流れ:

1. `Commander` が task を受ける
2. `Commander` が 1 本以上の Arms に work を割り当てる
3. `Shoulder` が方向づけを行う
4. `Elbow` があれば、さらに分解する
5. `Fingers` が subtasks を並列実行する
6. 上位 layer が result を統合する
7. `Commander` が最終 output を出す

## Status Reporting

status には必ず node identity を含めます。

例:

- `[A.Shoulder] received task`
- `[A.Middy] processing`
- `[A.Ringy] validation complete`
- `[A.Thumb] consolidating results`
- `[Commander] final output ready`

## Completion Criteria

task が complete と言えるのは、少なくとも次が揃ったときです。

- output が出ている
- results に整合性がある
- assumptions が書かれている
- unresolved issues が列挙されている

## Key Rule

上位 node が task を分解し、下位 node を並列 execution unit として使い、最後に result を統合します。

## Reading Map

- 次は [coordination-primitives.md](coordination-primitives.md) を読み、protocol, state, authority を確認します。
- 構造の話から durable behavior の話へ移るなら [profile-inheritance/README.md](profile-inheritance/README.md) を読みます。
- [lessons-learned.md](lessons-learned.md) は、core model が分かってから後で読みます。
