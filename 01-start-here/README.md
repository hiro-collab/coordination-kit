# Installation

Use this guide when you want to adopt `coordination-kit` in another workspace.

This repository is documentation and templates. There is no package-manager install step.

If you are browsing the repository for the first time, read this file before any deeper file in this folder.

## Read In This Order

1. [../README.md](../README.md)
2. [README.ja.md](README.ja.md) if the operators or judges need Japanese guidance
3. [workspace-isolation.md](workspace-isolation.md)
4. [../02-run-a-trial/README.md](../02-run-a-trial/README.md)
5. [../03-reference/README.md](../03-reference/README.md)

## Folder Map

- `../01-start-here/`: first-time adoption and environment setup
- `../02-run-a-trial/`: live execution guidance and preflight checks
- `../03-reference/`: stable rules and lessons learned
- `../04-maintainers/`: release and publishing tasks
- `../prompts/`: startup prompts for Commander and A.Shoulder
- `../templates/`: copyable templates grouped by run phase

## Standard Lower-Node Names

When the arm activates five finger lanes, use these names consistently:

- `Thumb`
- `Inddy`
- `Middy`
- `Ringy`
- `Pinky`

Use those names in task cards, file ownership, status updates, and handoff notes so the relationship between lanes stays visible.

## Recommended Options

### Option 1: Copy The Directory

Use this when you want a local editable copy inside a project and do not need automatic upstream tracking.

1. Copy `coordination-kit/` into your target workspace.
2. Keep it under a stable path such as `assets/coordination-kit/`.
3. Copy only the prompts and templates you need into the live run workspace.

### Option 2: Clone As A Standalone Reference Repo

Use this when you want to keep the kit versioned separately from the product repository.

```bash
git clone <repo-url> coordination-kit
```

Then keep run-specific files outside this repository and copy prompts or templates into the active project.

### Option 3: Add As A Git Submodule

Use this when the product repository should pin a kit revision and update it explicitly.

```bash
git submodule add <repo-url> assets/coordination-kit
git submodule update --init --recursive
```

## First 15 Minutes

1. Decide where the reusable kit will live.
2. Decide workspace isolation with [workspace-isolation.md](workspace-isolation.md).
3. Set directory responsibilities with [../03-reference/directory-conventions.md](../03-reference/directory-conventions.md).
4. Create the public brief from `../templates/01-setup/PUBLIC_TRIAL_BRIEF_TEMPLATE.md`.
5. Start Commander with `../prompts/COMMANDER_THREAD_PROMPT.md`.
6. If the user needs direct steering access, create a visible A.Shoulder thread with `../prompts/SHOULDER_THREAD_PROMPT.md`.
7. Copy the live-run templates you need into the project workspace, not back into the kit itself.

## Minimum Files To Start A New Trial

Read first:

- `../prompts/COMMANDER_THREAD_PROMPT.md`
- [../02-run-a-trial/README.md](../02-run-a-trial/README.md)
- [../03-reference/directory-conventions.md](../03-reference/directory-conventions.md)
- [workspace-isolation.md](workspace-isolation.md)

Usually copy these into the new run:

- `../templates/01-setup/PUBLIC_TRIAL_BRIEF_TEMPLATE.md`
- `../templates/03-checkpoints/RUN_MONITOR_TEMPLATE.md`
- `../templates/02-dispatch/COMMAND_DISPATCH_TEMPLATE.md`
- `../templates/02-dispatch/SEND_READY_PROMPT_TEMPLATE.md`
- `../templates/03-checkpoints/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- `../templates/04-handoff/SUBMISSION_PACKET_TEMPLATE.md`
- `../templates/04-handoff/FINAL_HANDOFF_TEMPLATE.md`
- `../templates/04-handoff/GAME_JUDGING_SCORECARD_TEMPLATE.md`
- `../templates/04-handoff/KIT_RETROSPECTIVE_TEMPLATE.md`

Add these when the run needs them:

- `../templates/01-setup/00_INDEX_TEMPLATE.md`
- `../templates/03-checkpoints/INTERFACE_CONTRACT_FREEZE_TEMPLATE.md`
- `../templates/03-checkpoints/VERIFICATION_RECORD_TEMPLATE.md`
- `../templates/03-checkpoints/LANGUAGE_AND_ONBOARDING_CHECKLIST_TEMPLATE.md`

## Suggested Directory Layout In The Target Workspace

```text
your-project/
  assets/
    coordination-kit/
  trial-ops/
  trial-runs/
    team-a/
    team-b/
```

If the kit stays external:

```text
coordination-kit/
your-project/
  trial-ops/
  trial-runs/
```

## Update Policy

- Treat the kit as reusable source material.
- Keep run-specific files outside the kit.
- If you improve the kit during a live trial, capture the idea and publish the kit update after judging unless a safety issue forces immediate change.

## Before Publishing Or Reusing Widely

- Read [../04-maintainers/publishing-checklist.md](../04-maintainers/publishing-checklist.md).
- Add a license if the repository will be public.
- Make sure all relative references still make sense when `coordination-kit` is the repository root.

## Next Docs

- Live execution: [../02-run-a-trial/README.md](../02-run-a-trial/README.md)
- Preflight check: [../02-run-a-trial/bootstrap-checklist.md](../02-run-a-trial/bootstrap-checklist.md)
- Japanese onboarding: [README.ja.md](README.ja.md)
- Standalone release prep: [../04-maintainers/publishing-checklist.md](../04-maintainers/publishing-checklist.md)

