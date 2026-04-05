# Bootstrap Checklist

Use this before starting a new coordination run.

Related docs:

- [Runbook](README.md)
- [Project Placement And Boundaries](../01-start-here/project-placement.md)
- [AI / System Reference](../03-reference/README.md)

## Project Files

- [ ] `AGENTS.md` exists and states the topology and responsibility split.
- [ ] Active node IDs are fixed, for example `A.Shoulder`, `A.Indy`, `B.Thumb`.
- [ ] Directory responsibilities are clear for global ops files, Arm files, and reusable assets.
- [ ] `00_INDEX.md` exists where file growth is likely, or an equivalent index exists.
- [ ] A project spec or mission brief exists and defines mission scope and acceptance criteria.
- [ ] `SHARED_NOTE.md` exists.
- [ ] `INTEGRATION.md` exists.
- [ ] `WORKING_MEMORY.Commander.md` exists.
- [ ] `WORKING_MEMORY.<active-node>.md` exists for the active Arm leads or lower nodes that need it.
- [ ] `LOG.Commander.md` exists.
- [ ] `LOG.<active-node>.md` exists for the active Arm leads or lower nodes that need it.
- [ ] `PERSONALITY.<node>.md` exists if persistent personality files are part of the run.
- [ ] `RUN_MONITOR.md` exists or is explicitly deferred for very small runs.
- [ ] `KIT_RETROSPECTIVE.md` exists or is queued for post-run use.

## Thread Setup

- [ ] Commander thread is active.
- [ ] A visible Shoulder thread exists if direct user interaction is required.
- [ ] The active Arm lead has authority to spawn and steer lower nodes.
- [ ] Commander retains mission scope and final sign-off.
- [ ] Required read-and-act instructions have been sent explicitly to the correct node.

## Before Parallel Execution

- [ ] Shared interfaces are written down in `SHARED_NOTE.md`.
- [ ] File ownership is written down in `SHARED_NOTE.md`.
- [ ] Lower-node names are treated as identifiers, not fixed specializations.
- [ ] Finger task cards include visible files to update.
- [ ] Critical files identify owner and intended readers where ambiguity would hurt.
- [ ] Start and finish updates to `WORKING_MEMORY.<node>.md` and `LOG.<node>.md` are required.
- [ ] If personality files are used, working memory is kept separate and does not update personality automatically.
- [ ] Each active Arm has its own writable workspace when isolation matters.
- [ ] Cross-arm visibility rules are written down.
- [ ] Mode labels, if used, are explicit and understandable to participants.

## Comparative Run Only

- [ ] Fairness constraints are fixed: same brief, same time budget, same tool budget, same judging rules.
- [ ] The public brief includes hard scope caps for time, asset volume, and implementation complexity.
- [ ] Each participant is asked to predict what user-facing judging criteria are likely to matter most.
- [ ] Midpoint playable is defined as a demonstrable end-to-end live run, not only a code path.
- [ ] First-play rule explanation and player guidance are planned in the primary human language.

## During Execution

- [ ] Monitoring checkpoints are scheduled.
- [ ] Commander records blockers and behavior-affecting assumption changes in `RUN_MONITOR.md`.
- [ ] Dispatch failures are surfaced quickly if a node did not act because no explicit instruction reached it.
- [ ] Collaboration quality is watched: each active node should have meaningful work and a visible handoff path.

## Before Final Sign-Off

- [ ] The active Arm lead has provided acceptance evidence and residual gaps.
- [ ] Commander has checked or rejected each acceptance item explicitly.
- [ ] Accepted deviations from the preferred stack or plan are recorded.
- [ ] Final handoff includes current state, known defects, launch method, evaluation focus, and explicit cuts where relevant.
- [ ] Kit improvement notes are captured for asset updates.

## Comparative Sign-Off Only

- [ ] Each participant has a completed judging scorecard.
- [ ] The winner or rework decision is written down with evidence.
