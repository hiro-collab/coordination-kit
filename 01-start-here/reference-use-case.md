# Reference Use Case

Use this file to understand the default example behind the rest of the kit.

English comes first in this file. A Japanese mirror follows later in the same document.

## Scenario

You want to ship a scoped software change with several agent lanes, but one person still needs visible control over what is happening.

Example task:

- add a user-facing settings panel
- keep an existing API contract stable
- verify the acceptance criteria before handoff

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

One reasonable division of work is:

- `Commander`: owns the mission brief, timing, and final integration
- `A.Shoulder`: steers implementation inside Arm A
- `A.Thumb`: updates data flow or backend integration
- `A.Indy`: updates UI and local validation
- `B.Shoulder`: owns verification scope and release readiness
- `B.Thumb`: checks acceptance criteria, docs, and handoff quality

The exact roles may change during the run. The important thing is that the IDs stay stable while the work emphasis stays visible.

## What Becomes Visible

Instead of relying on hidden chat state, the run writes visible coordination artifacts such as:

- `MISSION_BRIEF.md`
- `PERSONALITY.<node>.md` when persistent behavior policy is used
- `WORKING_MEMORY.<node>.md`
- `LOG.<node>.md`
- `INTEGRATION.md`
- `VERIFICATION_RECORD.md`
- `FINAL_HANDOFF.md`

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

たとえば次のように分けられます。

- `Commander`: mission brief、期限、最終統合を持つ
- `A.Shoulder`: Arm A 内の実装方針をまとめる
- `A.Thumb`: データフローや backend 連携を担当する
- `A.Indy`: UI 変更とローカル確認を担当する
- `B.Shoulder`: 検証観点と release readiness を持つ
- `B.Thumb`: acceptance criteria、docs、handoff 品質を確認する

この役割分担は固定ではありません。大事なのは、node id は安定させたまま、今どの node が何を重視して動いているかを見えるようにすることです。

### 何が可視化されるか

このキットでは、会話の中だけに状態を閉じ込めず、次のような書類を visible artifact として持ちます。

- `MISSION_BRIEF.md`
- 永続的な行動方針が必要なら `PERSONALITY.<node>.md`
- `WORKING_MEMORY.<node>.md`
- `LOG.<node>.md`
- `INTEGRATION.md`
- `VERIFICATION_RECORD.md`
- `FINAL_HANDOFF.md`

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
