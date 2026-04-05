# Coordination Primitives

Use this file when you want the kit explained as an operating model rather than only as a directory layout.

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
