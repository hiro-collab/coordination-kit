# Runbook

Use this when you have already chosen to run `coordination-kit` on a real task and now need the live-operation checklist.

If you want one concrete front-door scenario before reading the runbook, start with [../01-start-here/reference-use-case.md](../01-start-here/reference-use-case.md).

This kit supports:

- single-arm tests
- multi-arm runs
- competitive trials

Competitive browser-game comparison is one supported profile, not the default concept.

## What The User Does Here

Use this file when you are about to start a live run, not when you are still deciding whether the kit makes sense.

The user job in this phase is simple:

1. confirm the active topology and lane names
2. make sure writable workspaces and visible ops files exist
3. start Commander and any visible Shoulder threads
4. check that dispatch, status, verification, and handoff are happening visibly
5. keep final sign-off centralized

If those five things are not true yet, the run is not ready.

## Read Before Running

- [Getting Started](../01-start-here/README.md)
- [Reference Use Case](../01-start-here/reference-use-case.md)
- [Project Placement And Boundaries](../01-start-here/project-placement.md)
- [AI / System Reference](../03-reference/README.md)

## Quick Flow

1. Fix the topology and node IDs.
2. Bootstrap visible files and workspace boundaries.
3. Dispatch work across Arms and lower nodes.
4. Monitor, rebalance, and integrate visibly.
5. Sign off, hand off, and capture lessons.

## Japanese Summary

このファイルは、導入検討ではなく実運用中に開く runbook です。

ユーザーがやることは次の 5 つです。

1. どの Arm と node ID を動かすか決める
2. visible file と writable workspace をそろえる
3. file を置くだけで済ませず、明示的な dispatch を送る
4. drift や詰まりを見ながら再配分し、必要なら integration を固定する
5. sign-off 前に evidence をそろえ、最後に handoff と lessons を残す

## Topology Defaults

- Commander is the top-level coordinator.
- Arms are parallel work units.
- Each Arm may contain Shoulder, optional Elbow, and Fingers.
- Shoulder may directly control Fingers when Elbow is not needed.
- Names are identifiers, not fixed specializations.
- Higher layers decompose and integrate; lower layers execute.

## Common Profiles

### Single-Arm Test

Use this when you want to validate the operating model with one Arm first.

### Multi-Arm Parallel Run

Use this when the task benefits from parallel decomposition across Arms.

### Competitive Trial

Use this when you want side-by-side outputs under matched public constraints.

## Templates Used In This Phase

- Setup files: [../templates/01-setup/README.md](../templates/01-setup/README.md)
- Dispatch and tasking: [../templates/02-dispatch/README.md](../templates/02-dispatch/README.md)
- Checkpoints and verification: [../templates/03-checkpoints/README.md](../templates/03-checkpoints/README.md)
- Final handoff and evaluation: [../templates/04-handoff/README.md](../templates/04-handoff/README.md)

## Core Principles

- Keep `assets/coordination-kit` stable during active execution.
- Give each Arm its own writable workspace when isolation matters.
- Keep integration responsibility at the upper layer. Delegation does not remove accountability.
- Do not assume specialization by Arm or Finger name.
- Treat file creation as storage, not instruction delivery.
- If a node must act, send an explicit message naming the file and required action.
- If a human operator must forward that message, hand them the exact send-ready prompt body.
- Keep multi-node collaboration purposeful. The goal is not fewer nodes by default; the goal is visible contribution and integration.
- Use one primary human language for operator-facing, reviewer-facing, stakeholder-facing, or end-user-facing material within a given run.
- After the first integrated build or a major scope cut, redistribute work explicitly so validation, documentation, localization, and handoff support do not collapse silently into one node.
- If a checkpoint has a required visible update, schedule the reminder before the deadline and escalate before cutoff if the update is still missing.

## Recommended Layout

Use one of these layouts inside the current project root:

```text
run-workspaces/
  arm-a/
  arm-b/
```

```text
worktrees/
  arm-a/
  arm-b/
```

If the run is competitive, those arm directories may correspond to teams.

If you want the directory names to emphasize comparison, `trial-runs/` and `trial-ops/` are also acceptable.

Do not place active workspaces above the current project root.

Use `00_INDEX.md` in directories that may accumulate ad hoc files during the run.

## Roles

- User
  - starts visible threads
  - resolves scope disputes
  - reviews outputs when needed
- Commander
  - prepares the coordination files
  - locks mission scope and integration ownership
  - monitors active Arms
  - ensures explicit dispatch messages are sent when a node must read and act
  - records final sign-off
- Arm
  - acts as a parallel execution lane under Commander
- Shoulder
  - steers day-to-day execution inside its Arm
  - keeps visible files current
  - hands Commander an acceptance package
- Elbow
  - optionally decomposes within the Arm
  - may sit between Shoulder and Fingers
- Fingers
  - execute assigned work
  - report status with compact node IDs such as `A.Thumb`

## Phase 1: Bootstrap

1. Choose active Arms and node IDs before parallel execution.
2. Write one mission brief shared to all participating nodes.
3. If the run is comparative, also lock fairness constraints before work begins.
4. Set the primary human language for the run.
5. Copy the setup templates into each active workspace.
6. Create `00_INDEX.md` files where visibility would otherwise sprawl.
7. Create `SHARED_NOTE.md`, `INTEGRATION.md`, `WORKING_MEMORY.<node>.md`, and `LOG.<node>.md` for active nodes.
8. Create `PERSONALITY.<node>.md` files if persistent personality is part of the run.
9. Create `RUN_MONITOR.md` when the run is long, parallel, or risky enough to need checkpoint tracking.
10. Prepare a `SUBMISSION_PACKET.md` draft path before final handoff if formal handoff is expected.
11. Decide where `VERIFICATION_RECORD.md`, `INTERFACE_CONTRACT_FREEZE.md`, and any language or onboarding checklists will live if they are needed.
12. Send explicit dispatch messages for required read-and-act steps. Do not assume file creation alone will trigger work.

## Optional Competitive Browser-Game Profile

If the run is a side-by-side browser-game comparison, apply the following additional rules and use `PUBLIC_TRIAL_BRIEF_TEMPLATE.md` instead of only the generic mission brief.

### Comparative Principles

- Give each team its own writable workspace.
- Apply the same mission, time budget, tools, and public constraints to both teams.
- Judge the shipped game separately from the coordination process.
- Do not lock an overly precise judging rubric in advance unless the trial specifically needs it.
- Ask teams to state their own guess about what users will value before implementation locks.
- Use one official wall-clock in the local timezone and record absolute times for every checkpoint.

### Public Brief Design Rules

The public brief should be strong enough to control scope without revealing the final scoring weights.
The public brief should be strong enough to control scope without pretending to settle every judging tradeoff in advance.

Recommended hard limits:

- one-screen or one-arena game
- one primary mechanic and at most one secondary mechanic
- single-player only
- no backend, login, matchmaking, or persistence service
- no custom asset production pipeline during the run
- small local asset set only
- playable within 60 to 180 seconds
- implementation timebox fixed before work starts
- midpoint and freeze times fixed as absolute local times before work starts

Recommended brief style:

- give a theme and required player action
- define non-goals explicitly
- define what "playable" means
- define where the player sees the rule explanation in the first few seconds
- require player-facing onboarding in the primary human language for the run
- require each team to submit its own prediction of likely user-desired judging criteria

Midpoint standard:

- midpoint playable should mean one live end-to-end run can be demonstrated by the checkpoint
- a code path existing is not enough

## Phase 2: Live Monitoring

Use checkpoints whenever the run is long enough or risky enough that silent drift would hurt.

At each checkpoint, record:

- current scope
- visible artifacts produced
- blockers
- risky assumptions
- whether required dispatch messages were actually sent and acknowledged
- whether the collaboration setup is helping multiple nodes contribute meaningfully
- which nodes are active for the next phase
- whether redistribution or re-entry commands were sent after new evidence changed the shipping scope
- whether a reminder or escalation must be sent before the next hard deadline

If the run is comparative, also record whether fairness constraints still match across participants.

After the first integrated build or midpoint:

- freeze the canonical contract files for the next phase
- if lanes have drifted, write an interface-contract freeze note naming the authoritative file and owner
- decide which nodes stay on implementation, which nodes are recalled, and which nodes switch to verification, docs, localization, or handoff support
- write that redistribution visibly
- send explicit commands for that redistribution
- record one visible verification result for what was actually tested end to end

Before final handoff:

- require a team-local or arm-local submission packet that mirrors the final handoff fields
- require a visible verification record for the current state when playability or operability is being claimed
- do not let the only copy of the handoff content live in scattered logs or working-memory notes

## Phase 3: Handoff And Evaluation

1. Freeze further changes.
2. Perform Commander sign-off against the written acceptance criteria.
3. If the run is comparative, review each output with a separate scorecard.
4. Record evidence for strengths, weaknesses, disqualifying issues, and budget overruns.
5. Compare the shipped result against any predicted user-value criteria if that exercise was used.
6. Decide accept, rework, winner, or tie based on written evidence rather than thread impressions.
7. When useful, record separate judgments for product quality, operations quality, and overall result.

## Phase 4: Improvement Loop

1. Fill in `KIT_RETROSPECTIVE.md`.
2. Separate product failure from coordination-kit failure.
3. List which asset files should change.
4. Patch the kit after active execution is complete.
5. Preserve rejected ideas so the next run does not re-debate the same issue blindly.
