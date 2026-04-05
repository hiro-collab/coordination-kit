# Coordination Primitives

Use this file when you want the kit explained as an operating model rather than only as a directory layout.

For a user, this file explains what should happen after the setup prompt: how work moves, where truth lives, and who gets to decide.

In user terms:

- `protocol` answers: "What do I tell the AI to do?"
- `state` answers: "Which file should I check?"
- `policy` answers: "Who is allowed to decide?"

The practical loop is:

1. assign an owner
2. dispatch explicit work
3. wait for acknowledgement
4. read visible reports
5. integrate or escalate
6. sign off against written criteria

If those six actions are unclear, the run will drift.

English comes first in this file. A Japanese mirror appears later in the same document.

This reference groups the kit into three layers:

- `protocol`: how nodes explicitly move work
- `state`: where visible truth is stored
- `policy`: who is allowed to decide what

In short:

- protocol moves work
- state stores truth
- policy decides authority

## 1. Protocol

Here, `protocol` does not mean a network protocol.
It means the visible coordination actions that nodes use to run work together.

### Core Protocol Verbs

#### `assign`

- Meaning: an upper layer chooses who owns a task or subtask
- Typical owner: `Commander`, `Shoulder`, or `Elbow`
- Visible artifact: mission brief, task card, shared note, or run monitor
- Complete when: ownership is explicit and the responsible node is named

#### `dispatch`

- Meaning: tell a specific node to read something and act
- Typical owner: whoever is delegating
- Visible artifact: dispatch file plus an explicit message to the target thread
- Complete when: the message names the file and required action

#### `acknowledge`

- Meaning: confirm that a dispatch was seen and understood
- Typical owner: the receiving node
- Visible artifact: reply in thread, log entry, or shared-note update
- Complete when: the receiver confirms scope, constraints, or next action

#### `report`

- Meaning: publish current status, blockers, risks, or evidence
- Typical owner: any active node
- Visible artifact: `LOG.*.md`, `WORKING_MEMORY.*.md`, `RUN_MONITOR.md`, or verification records
- Complete when: another reader can tell current status without guessing hidden context

#### `integrate`

- Meaning: combine outputs from lower lanes into a coherent next state
- Typical owner: `Shoulder`, `Elbow`, or `Commander`
- Visible artifact: `INTEGRATION.md`, frozen interface notes, merged deliverables
- Complete when: the authoritative combined result is named and visible

#### `handoff`

- Meaning: transfer responsibility for review, next-step work, or final delivery
- Typical owner: lower lane to upper lane, or one phase to the next
- Visible artifact: submission packet, handoff note, verification record
- Complete when: the receiving side can continue without reconstructing context from scattered logs

#### `sign-off`

- Meaning: accept or reject the current integrated state against written criteria
- Typical owner: `Commander` or the designated reviewer
- Visible artifact: final handoff or sign-off record
- Complete when: acceptance status and rationale are visible

#### `escalate`

- Meaning: push a problem upward because local authority is insufficient
- Typical owner: any node that hits a scope, risk, or dependency boundary
- Visible artifact: blocker note, run-monitor entry, explicit escalation message
- Complete when: the higher authority is explicitly asked to decide

### Protocol Rules

- Writing a file is not the same as dispatching work.
- Dispatch should name both the file and the required action.
- Acknowledgement should happen before long or risky delegated work disappears into silence.
- Reports should prefer visible artifacts over private reconstruction.
- Sign-off should happen against written criteria, not thread mood.

## 2. State

`state` means the visible records that tell the team what is true right now.

The kit separates state by lifespan and authority.

### Persistent State

- `PERSONALITY.<node>.md`
- Meaning: stable behavior policy across runs or sessions
- Authority: explicit external review only
- Must not contain: disposable task logs

### Run-Global State

- `MISSION_BRIEF.md`
- `INTEGRATION.md`
- `RUN_MONITOR.md`
- `SHARED_NOTE.md`
- Meaning: the current shared truth for the run
- Authority: usually `Commander`, with updates from lower lanes as appropriate

### Node-Local Working State

- `WORKING_MEMORY.<node>.md`
- `LOG.<node>.md`
- Meaning: disposable local context, progress, and reasoning breadcrumbs
- Authority: the owning node
- Rule: local state may inform the run, but it does not silently rewrite policy

### Evidence And Handoff State

- `VERIFICATION_RECORD.md`
- `SUBMISSION_PACKET.md`
- `FINAL_HANDOFF.md`
- Meaning: what was actually tested, what is being handed over, and what was accepted
- Authority: whoever owns review or final delivery for that phase

### State Rules

- Persistent state and working state must stay separate.
- Run-global state should name the current authoritative file when ambiguity exists.
- If a claim matters, there should be visible evidence somewhere in state.
- If a new reader cannot determine current truth from visible files, the state model is failing.

## 3. Policy

`policy` means the authority rules for decomposition, decision-making, escalation, and acceptance.

### Default Authority Model

#### Commander

- owns mission scope
- chooses active Arms
- owns cross-Arm integration and final sign-off
- decides when to rebalance or freeze work

#### Arm

- is one parallel team lane under Commander
- carries a share of the run without owning the whole mission by default

#### Shoulder

- steers day-to-day execution inside one Arm
- decomposes local work when possible
- keeps Arm-visible artifacts current
- escalates when Arm-local authority is insufficient

#### Elbow

- is optional
- performs additional decomposition between Shoulder and Fingers
- helps when one Shoulder-to-Fingers step is too coarse

#### Fingers

- execute concrete assigned tasks
- report status, blockers, and evidence with stable node IDs
- do not silently assume global authority

### Policy Triggers

#### Rebalance

Rebalance when:

- one lane is overloaded
- integration debt is growing
- verification or docs work is collapsing into the implementation lane
- new evidence changes the shipping plan

#### Escalate

Escalate when:

- acceptance criteria conflict with current implementation
- an Arm needs another Arm's contract changed
- time, scope, or quality goals cannot all be satisfied locally
- a required dispatch or acknowledgement is missing near a deadline

#### Sign-Off

Sign-off should require:

- an integrated artifact
- visible evidence for important claims
- unresolved issues listed explicitly
- acceptance or rejection written by the authorized reviewer

### Policy Principles

- structure is fixed, meaning is dynamic
- roles are not fixed by Arm or Finger name
- stable personality is separate from task-local behavior
- delegation does not remove upper-layer accountability
- visible coordination is preferred over implied coordination

## Reading Map

Use this file together with:

- [agent-topology.md](agent-topology.md) for hierarchy and naming
- [memory-and-personality.md](memory-and-personality.md) for persistent versus disposable state
- [directory-conventions.md](directory-conventions.md) for where each artifact should live
- [../02-runbook/README.md](../02-runbook/README.md) for the execution sequence

## Japanese

このファイルは、この kit を単なるフォルダ構成ではなく、運用モデルとして理解したいときに読むための基準文書です。

利用者の言葉で言えば:

- `protocol` は「AI に何をさせるか」
- `state` は「どのファイルを見ればよいか」
- `policy` は「だれが決めてよいか」

ユーザー目線では、次の 6 動作で見れば実務上は十分です。

1. owner を assign する
2. 明示的に dispatch する
3. acknowledge を待つ
4. visible report を読む
5. integrate するか escalate する
6. written criteria に対して sign-off する

この 6 動作が曖昧な run は、途中で drift しやすくなります。

この reference では、kit を次の 3 層に分けて説明します。

- `protocol`: node 間で仕事をどう動かすか
- `state`: いま何が真実かをどこに保存するか
- `policy`: 誰が何を決められるか

短く言うと:

- protocol は仕事を動かす
- state は真実を保存する
- policy は authority を決める

## 1. Protocol

ここでいう `protocol` は、ネットワーク protocol の意味ではありません。
複数 node が協調して動くための、見える coordination action の集合です。

### Core Protocol Verbs

#### `assign`

- 意味: 上位 layer が task や subtask の owner を決める
- 主な owner: `Commander`, `Shoulder`, `Elbow`
- 主な artifact: mission brief, task card, shared note, run monitor
- 完了条件: ownership と responsible node が明示されている

#### `dispatch`

- 意味: 特定 node に「これを読んで、これをやれ」と伝える
- 主な owner: delegation している側
- 主な artifact: dispatch file と target thread への明示メッセージ
- 完了条件: message の中で file と required action が明示されている

#### `acknowledge`

- 意味: dispatch を見て理解したことを確認する
- 主な owner: 受信した node
- 主な artifact: thread reply, log entry, shared-note update
- 完了条件: receiver が scope, constraint, next action を返している

#### `report`

- 意味: current status, blocker, risk, evidence を publish する
- 主な owner: active な任意 node
- 主な artifact: `LOG.*.md`, `WORKING_MEMORY.*.md`, `RUN_MONITOR.md`, verification record
- 完了条件: 他の reader が hidden context を推測せずに current status を把握できる

#### `integrate`

- 意味: 下位 lane の output を、次の authoritative state に統合する
- 主な owner: `Shoulder`, `Elbow`, `Commander`
- 主な artifact: `INTEGRATION.md`, interface freeze note, merged deliverable
- 完了条件: authoritative な統合結果が visible に指定されている

#### `handoff`

- 意味: review, next-step work, final delivery の responsibility を渡す
- 主な owner: lower lane から upper lane、または phase 間の受け渡し
- 主な artifact: submission packet, handoff note, verification record
- 完了条件: scattered log を掘らなくても受け手が次に進める

#### `sign-off`

- 意味: 書かれた criteria に照らして current integrated state を accept または reject する
- 主な owner: `Commander` または designated reviewer
- 主な artifact: final handoff, sign-off record
- 完了条件: acceptance status と rationale が visible に残っている

#### `escalate`

- 意味: local authority では決められない問題を上位へ上げる
- 主な owner: scope, risk, dependency の境界に当たった任意 node
- 主な artifact: blocker note, run-monitor entry, explicit escalation message
- 完了条件: 上位 authority に decision request が明示されている

### Protocol Rules

- file を書くことと、仕事を dispatch することは別です。
- dispatch では file 名と required action を両方明示します。
- 長い仕事や risky な delegated work では、silence に入る前に acknowledge が必要です。
- report は private な再構成より visible artifact を優先します。
- sign-off は thread の雰囲気ではなく、written criteria に対して行います。

## 2. State

`state` とは、「いま何が真実か」を visible に保持している記録です。

この kit では、state を lifespan と authority で分けます。

### Persistent State

- `PERSONALITY.<node>.md`
- 意味: run や session をまたいで保つ stable behavior policy
- authority: 明示的な external review のみ
- 入れてはいけないもの: disposable task log

### Run-Global State

- `MISSION_BRIEF.md`
- `INTEGRATION.md`
- `RUN_MONITOR.md`
- `SHARED_NOTE.md`
- 意味: run 全体で共有される current truth
- authority: 通常は `Commander`、必要に応じて lower lane から update が入る

### Node-Local Working State

- `WORKING_MEMORY.<node>.md`
- `LOG.<node>.md`
- 意味: disposable な local context, progress, reasoning breadcrumb
- authority: その node 自身
- rule: local state は run の判断材料にはなってよいが、policy を黙って書き換えてはいけない

### Evidence And Handoff State

- `VERIFICATION_RECORD.md`
- `SUBMISSION_PACKET.md`
- `FINAL_HANDOFF.md`
- 意味: 何を検証したか、何を引き渡すか、何を accept したか
- authority: その phase の review または final delivery owner

### State Rules

- persistent state と working state は分ける
- run-global state で曖昧さが出るなら、authoritative file を明記する
- 重要な claim には visible evidence が必要
- new reader が visible file から current truth を判断できないなら、state model が壊れている

## 3. Policy

`policy` とは、decomposition, decision-making, escalation, acceptance に関する authority rule です。

### Default Authority Model

#### Commander

- mission scope を持つ
- active Arm を選ぶ
- cross-Arm integration と final sign-off を持つ
- rebalance や freeze のタイミングを決める

#### Arm

- Commander 配下の 1 本の parallel team lane
- whole mission 全体を持つのではなく、その run の一部を担う

#### Shoulder

- 1 つの Arm の日々の execution を steer する
- 可能なら local work を分解する
- Arm 内の visible artifact を更新する
- Arm-local authority で足りないときは escalate する

#### Elbow

- optional
- Shoulder と Fingers の間で追加の decomposition を行う
- Shoulder から Fingers への 1 段が粗すぎるときに使う

#### Fingers

- concrete assigned task を実行する
- stable node ID で status, blocker, evidence を report する
- global authority を暗黙に仮定しない

### Policy Triggers

#### Rebalance

次のときは rebalance を検討します。

- 1 つの lane が過負荷になっている
- integration debt が増えている
- verification や docs の仕事が implementation 側へ潰れている
- 新しい evidence によって shipping plan が変わった

#### Escalate

次のときは escalate します。

- acceptance criteria と current implementation が衝突している
- ある Arm が別の Arm の contract 変更を必要としている
- time, scope, quality を local では両立できない
- deadline 近くで required dispatch や acknowledgement が欠けている

#### Sign-Off

sign-off には少なくとも次が必要です。

- integrated artifact
- 重要 claim に対する visible evidence
- unresolved issue の明示
- authorized reviewer による acceptance または rejection の記録

### Policy Principles

- structure is fixed, meaning is dynamic
- roles are not fixed by Arm or Finger name
- stable personality is separate from task-local behavior
- delegation does not remove upper-layer accountability
- visible coordination is preferred over implied coordination

## Reading Map

このファイルは次の文書と一緒に読む想定です。

- [agent-topology.md](agent-topology.md): hierarchy と naming
- [memory-and-personality.md](memory-and-personality.md): persistent state と disposable state の分離
- [directory-conventions.md](directory-conventions.md): artifact をどこに置くか
- [../02-runbook/README.md](../02-runbook/README.md): 実行順序と運用手順
