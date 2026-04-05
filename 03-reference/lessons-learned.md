# Lessons Learned

- Owner: Commander / kit maintainer
- Readers: user, Commander, visible A.Shoulder threads, future operators

Use this as the maintainer-facing record of rules that survived real runs.

Most items below are generic carry-forward rules. Trial-only notes are kept in a separate section so they do not accidentally redefine the default model.

## Generic Lessons

### What Worked

- Separate writable workspaces kept active lanes isolated and avoided polluting unrelated directories.
- Shared templates made it easier to compare operating-model quality across runs.

### What Needed Improvement

- Writing a file was often mistaken for dispatching work; explicit thread-level commands were still required.
- Telling an operator "the prompt is in that file" was still too indirect; forwarders needed the actual send-ready body.
- The directory and markdown layout was flexible, but file ownership and readership were not obvious enough.
- Final handoff content became clear only late in the run and should have been standardized earlier.
- The issue in multi-node execution was not headcount by itself, but whether every node had clear work, visibility, and coordination.
- Teams needed a visible post-checkpoint redistribution step so completed or partially idle nodes could shift into verification, docs, localization, or handoff support.
- Teams needed visible interface-contract freeze notes when integration drifted.

### Rules To Carry Forward

- Use a visible A.Shoulder thread when the user needs to steer it directly.
- Treat writing a file and dispatching a task as separate steps; send an explicit message naming the file and required action.
- If a human operator must relay the instruction, give them the full send-ready prompt body in addition to any reference file.
- Create shared coordination files before finger spawning begins.
- Make file ownership explicit before collaborative execution starts.
- Add `Owner:` and `Readers:` to human-facing markdown where ambiguity would cause delays.
- Add `00_INDEX.md` in directories that may grow during a run so new files remain navigable.
- Treat hidden thread context as non-authoritative unless echoed into visible files or status.
- Freeze canonical contract files after the first integrated build or checkpoint when multiple lanes have started to drift.
- Write visible redistribution after checkpoint changes so every active node either has a new role or is explicitly released.
- Schedule phase-end reminders and escalations before required visible updates are late.
- Require final handoff to be submitted in a fixed visible format.
- Evaluate multi-node collaboration by contribution quality and coordination quality, not by assuming fewer nodes are automatically better.

### Generic Failure Checks

- A.Shoulder becomes only an advisor while Commander micro-manages fingers.
- Fingers complete code work without updating visible state.
- Shared assumptions change without `SHARED_NOTE.md` updates.
- A file is updated, but no responsible thread is explicitly told to read it and act.
- A send-ready prompt exists only as a file reference, so the human forwarder still has to reconstruct what to send.
- Handoff is treated as implicit rather than submitted in a fixed visible format.
- Some nodes remain idle because ownership, dependencies, or required inputs were not made explicit.
- Some nodes finish their first slice but are never recalled or reassigned after checkpoint changes.
- Shared boundaries drift, but no visible contract freeze names the authoritative file and owner.

## Competitive Browser-Game Trial Notes

These notes are useful when the run is explicitly a judged browser-game comparison. They are not the generic default.

- Visible `LIVE_STATUS_BOARD.md` updates made it possible to compare team progress without relying on hidden thread state.
- Time checkpoints such as plan lock, midpoint, feature freeze, and submission cutoff gave Commander clear intervention moments.
- Shared templates made it possible to collect both game-quality judgment and operating-model judgment from the same run.
- `midpoint playable` was too easy to interpret loosely; it should mean a demonstrable end-to-end live run.
- Judge-facing materials and first-play guidance needed stronger Japanese support.
- Teams needed a team-local submission packet before the final shared-board update so handoff content did not have to be reconstructed from scattered files.
- Teams also needed visible proof-of-play records when playable claims were disputed.
- Record game winner, operations winner, and overall result separately when those judgments diverge.
- Use the primary human language for judge-facing summaries and player-facing onboarding.

### Trial Failure Checks

- Midpoint is marked complete without a visible end-to-end run.
- The player can technically launch the build but cannot quickly find the rule explanation.
- A team claims playable progress, but there is no visible verification record showing what was actually tested.

## Pending Follow-Up

- Merge the forthcoming Team Alpha retrospective into these lessons once it is visible.
- Merge the forthcoming Team Blabo retrospective into these lessons once it is visible.
- Re-check whether the new dispatch, handoff, and directory rules cover the concrete failures the teams report.
