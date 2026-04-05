# Trial Runbook

Use this when two teams are building separate browser games from the same coordination kit and you want to compare both outputs fairly.

## Read Before Running

- [Getting Started](../getting-started.md)
- [Workspace Isolation](workspace-isolation.md)
- [Directory Conventions](../reference/directory-conventions.md)

## Quick Flow

1. Bootstrap the run and lock fair public constraints.
2. Monitor live progress with visible checkpoints and explicit dispatch.
3. Freeze changes and judge the shipped outputs.
4. Update the kit only after judging is complete.

## Core Principles

- Keep `assets/coordination-kit` stable during active execution.
- Give each team its own writable workspace.
- Apply the same mission, time budget, tools, and public constraints to both teams.
- Let Commander monitor fairness and completion, not micro-manage implementation.
- Judge the shipped game separately from the coordination process.
- Do not lock an overly precise judging rubric in advance unless the trial specifically needs it.
- Ask teams to state their own guess about what users will value before implementation locks.
- Use one official wall-clock in the local timezone and record absolute times for every checkpoint.
- Treat file creation as storage, not instruction delivery. If a node must act, send an explicit message naming the file and the required action.
- If a user or another human operator must forward that message, hand them the exact send-ready prompt body, not only the file path.
- Use one primary human language for judge-facing documents and first-play player guidance.
- Keep multi-node collaboration purposeful. The goal is not fewer nodes by default; the goal is that every active node has meaningful work and visible coordination.
- After the first integrated build or a major scope cut, redistribute work explicitly so verification, documentation, localization, and handoff support do not collapse silently back to Shoulder.
- If a checkpoint has a required visible update, schedule the reminder before the deadline and escalate before cutoff if the update is still missing.

## Recommended Layout

Use one of these layouts inside the current project root:

```text
trial-runs/
  team-a/
  team-b/
```

```text
worktrees/
  team-a/
  team-b/
```

Do not place team workspaces above the current project root.

Use `00_INDEX.md` in directories that may accumulate ad hoc files during the run.

## Roles

- User
  - starts visible threads
  - resolves scope disputes
  - co-judges the results with Commander
- Commander
  - prepares the coordination files
  - locks fairness constraints
  - monitors both teams
  - ensures explicit dispatch messages are sent when a node must read and act
  - records the final judging and kit updates
- A.Shoulder or team lead
  - steers day-to-day execution inside its assigned team
  - keeps visible files current
  - hands Commander an acceptance package

## Phase 1: Bootstrap

1. Choose workspace isolation before any team starts writing files.
2. Write one public trial brief that both teams receive.
3. Set the primary human language for judge-facing documents and player-facing onboarding.
4. Copy the public templates into each active trial workspace.
5. Create `00_INDEX.md` files where visibility would otherwise sprawl.
6. Lock the game brief, non-goals, timebox, and allowed tools.
7. Create `RUN_MONITOR.md`.
8. Create one judging scorecard per team.
9. Make sure both teams know they must not inspect the competing team's output until judging starts.
10. Write the official start time, midpoint, feature-freeze time, and submission cutoff before work begins.
11. Send explicit dispatch messages for required read-and-act steps. Do not assume file creation alone will trigger work.
12. Prepare a team-local `SUBMISSION_PACKET.md` or equivalent draft path before the final handoff phase begins.
13. When Commander asks a human to relay a message, prepare a send-ready prompt block that can be pasted directly into the destination thread.
14. Decide where `VERIFICATION_RECORD.md`, `LANGUAGE_AND_ONBOARDING_CHECKLIST.md`, and any `INTERFACE_CONTRACT_FREEZE.md` files will live if they are needed.

## Public Brief Design Rules

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

Use four checkpoints unless the run is extremely short:

- T0 bootstrap complete
- T1 plan locked
- T2 mid-build
- T3 pre-judge handoff

At each checkpoint, record:

- current scope
- visible artifacts produced
- blockers
- risky assumptions
- whether fairness constraints still match across teams
- whether required dispatch messages were actually sent and acknowledged
- whether the collaboration setup is helping multiple nodes contribute meaningfully
- which nodes are active for the next phase
- whether redistribution or re-entry commands were sent after new evidence changed the shipping scope
- whether a reminder or escalation must be sent before the next hard deadline

After the first integrated build or midpoint:

- freeze the canonical contract files for the next phase
- if lanes have drifted, write an interface-contract freeze note naming the authoritative file and owner
- decide which nodes stay on implementation, which nodes are recalled, and which nodes switch to verification, docs, localization, or handoff support
- write that redistribution visibly
- send explicit commands for that redistribution
- record one visible verification result for what was actually played end to end

Before final handoff:

- require a team-local submission packet that mirrors the final shared-board fields
- require a visible verification record for the current playable state, known fail path, and restart path when relevant
- do not let the only copy of the handoff content live in scattered logs or working-memory notes

## Phase 3: Judging

1. Freeze further changes.
2. Review each game with a separate scorecard.
3. Score independently first, then reconcile with the user.
4. Record evidence for strengths, weaknesses, disqualifying issues, and budget overruns.
5. Compare the shipped game against the team's own predicted user-value criteria.
6. Decide winner, tie, or rework based on written evidence rather than thread impressions.
7. When useful, record separate judgments for game quality, operations quality, and overall result.

## Phase 4: Kit Improvement Loop

1. Fill in `KIT_RETROSPECTIVE.md`.
2. Separate "game lost because of product decisions" from "game lost because the coordination kit failed."
3. List which asset files should change.
4. Patch the kit after judging is complete.
5. Preserve rejected ideas so the next run does not re-debate the same issue blindly.
