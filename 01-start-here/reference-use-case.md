# Reference Use Case

Use this file to understand the default example behind the rest of the kit.

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
