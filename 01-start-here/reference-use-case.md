# Reference Use Case

Use this file to understand the default example behind the rest of the kit.

English comes first in this file. A Japanese mirror follows later in the same document.

## Scenario

You want to ship a scoped software change with several agent lanes, but one person still needs visible control over what is happening.

Example task:

- add a user-facing settings panel
- keep an existing API contract stable
- verify the acceptance criteria before handoff

Example user instruction:

```text
Use coordination-kit for this feature work.
Act as Commander.
Before creating anything, confirm that you can read the kit path and that you will write only inside this project's run directories.
Create Arm A and Arm B as two team lanes so implementation and verification can move in parallel.
Use A.Shoulder and B.Shoulder as the first acting threads inside those lanes.
Keep the API stable, keep handoff visible, and keep final sign-off centralized.
```

## Example Topology

```text
Commander
  Arm A
    A.Shoulder
    A.Thumb
    A.Indy
  Arm B
    B.Shoulder
    B.Thumb
```

One reasonable early state is:

- `Commander`: owns the mission brief, timing, and final integration
- `Arm A`: one stable team lane under Commander, currently carrying more implementation-heavy work
- `A.Shoulder`: coordinates current work inside Arm A
- `A.Thumb`: currently updates data flow or backend integration
- `A.Indy`: currently updates UI and local validation
- `Arm B`: another stable team lane under Commander, currently carrying more verification or handoff-heavy work
- `B.Shoulder`: coordinates current work inside Arm B
- `B.Thumb`: currently checks acceptance criteria, docs, or handoff quality

The exact roles may change during the run. The important thing is that the IDs stay stable while the work emphasis stays visible. Arm names are team identities, not permanent departments.

If it helps, read Arm names aloud like team call-signs:

- `Arm A` -> `Alpha`
- `Arm B` -> `Blabo`

## What Becomes Visible

Instead of relying on hidden chat state, the run writes visible coordination artifacts such as:

- `MISSION_BRIEF.md`
- `PERSONALITY.<node>.md` when persistent behavior policy is used
- `WORKING_MEMORY.<node>.md`
- `LOG.<node>.md`
- `INTEGRATION.md`
- `VERIFICATION_RECORD.md`
- `FINAL_HANDOFF.md`

## What The User Should Notice

- the user can tell who currently owns scope and sign-off
- the user can see which lane is implementing and which lane is checking
- the user can intervene without reconstructing hidden context from chat
- the final delivery is backed by visible evidence instead of memory

## Why This Kit Helps

- one person can supervise several active lanes without losing ownership
- implementation and verification can proceed in parallel
- handoff and sign-off are based on visible files rather than memory
- reusable coordination policy stays separate from run-local writable files

## When This Example Generalizes Well

This same pattern also fits:

- documentation or localization runs
- compare-and-choose exploration across two Arms
- human-plus-agent review flows where explicit acceptance evidence matters

If you only need one agent and no formal handoff, this kit is probably heavier than necessary.

## Japanese

このファイルは、このキットをどういう場面で使う想定なのかを最短で掴むための説明です。

### 想定シナリオ

複数の agent lane を使って、ある程度まとまったソフトウェア変更を進めたい。
ただし、最終的な責任と見通しは 1 人の人間または上位 thread が持っていたい。

例:

- 設定画面を追加する
- 既存 API 契約は壊さない
- 最終 handoff 前に acceptance criteria を明示的に確認する

たとえばユーザーは次のように言います。

```text
この機能追加では coordination-kit を使う。
あなたは Commander として動く。
何か作る前に、kit の read path と、この project 側の run directory だけに書くことを確認する。
実装と検証が並列に進むように、Arm A と Arm B の 2 つの team lane を作る。
その lane の最初の acting thread は A.Shoulder と B.Shoulder にする。
API は壊さず、handoff を visible にし、最終 sign-off は 1 か所に残す。
```

### 例となるトポロジ

```text
Commander
  Arm A
    A.Shoulder
    A.Thumb
    A.Indy
  Arm B
    B.Shoulder
    B.Thumb
```

たとえば run の初期状態として、次のように分かれます。

- `Commander`: mission brief、期限、最終統合を持つ
- `Arm A`: Commander 配下の安定した team lane で、この時点では実装寄りの作業が多い
- `A.Shoulder`: Arm A 内の現在の作業を調整する
- `A.Thumb`: この時点ではデータフローや backend 連携を進める
- `A.Indy`: この時点では UI 変更とローカル確認を進める
- `Arm B`: Commander 配下の別の安定した team lane で、この時点では検証や handoff 寄りの作業が多い
- `B.Shoulder`: Arm B 内の現在の作業を調整する
- `B.Thumb`: この時点では acceptance criteria、docs、handoff 品質を確認する

この役割分担は固定ではありません。大事なのは、node id は安定させたまま、今どの node が何を重視して動いているかを見えるようにすることです。Arm 名は担当部署ではなく、team identity です。

会話上は `Arm A` を `Alpha`、`Arm B` を `Blabo` のような team callsign として読むとイメージしやすいです。

### 何が可視化されるか

hidden chat state に頼らず、たとえば次のような coordination artifact が visible file として残ります。

- `MISSION_BRIEF.md`
- 永続的な行動方針が必要なら `PERSONALITY.<node>.md`
- `WORKING_MEMORY.<node>.md`
- `LOG.<node>.md`
- `INTEGRATION.md`
- `VERIFICATION_RECORD.md`
- `FINAL_HANDOFF.md`

### ユーザーから見て分かること

- いま誰が scope と sign-off を持っているかが分かる
- どの lane が実装寄りで、どの lane が確認寄りかが分かる
- hidden chat を復元しなくても途中介入しやすい
- 最終成果物の根拠が記憶ではなく visible evidence になる

### このキットが効く理由

- 1 人が複数 lane を監督しても、責任の所在を失いにくい
- 実装と検証を並行に進めやすい
- handoff や sign-off を会話の記憶ではなく visible file に残せる
- 再利用可能な coordination policy と、その run 限りの作業ファイルを分離できる

### この例から横展開しやすい場面

- docs / localization の並行作業
- 2 つの Arm を使った explore and compare
- human-in-the-loop の review flow

逆に、単発の小タスクを 1 agent だけで終えるなら、このキットは少し重いです。
