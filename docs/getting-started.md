# Getting Started

Use this guide when you want to adopt `coordination-kit` in another workspace.

This repository is documentation and templates. There is no package-manager install step.

## Read In This Order

1. [../README.md](../README.md)
2. [guides/workspace-isolation.md](guides/workspace-isolation.md)
3. [reference/directory-conventions.md](reference/directory-conventions.md)
4. [guides/runbook.md](guides/runbook.md)
5. [ja/getting-started.md](ja/getting-started.md) if the operators or judges need Japanese guidance

## Choose How To Adopt The Kit

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
2. Decide workspace isolation with [guides/workspace-isolation.md](guides/workspace-isolation.md).
3. Set directory responsibilities with [reference/directory-conventions.md](reference/directory-conventions.md).
4. Create the public brief from `../templates/PUBLIC_TRIAL_BRIEF_TEMPLATE.md`.
5. Start Commander with `../prompts/COMMANDER_THREAD_PROMPT.md`.
6. If the user needs direct steering access, create a visible A.Shoulder thread with `../prompts/SHOULDER_THREAD_PROMPT.md`.
7. Copy the live-run templates you need into the project workspace, not back into the kit itself.

## Minimum Files To Start A New Trial

Read first:

- `../prompts/COMMANDER_THREAD_PROMPT.md`
- [guides/runbook.md](guides/runbook.md)
- [reference/directory-conventions.md](reference/directory-conventions.md)
- [guides/workspace-isolation.md](guides/workspace-isolation.md)

Usually copy these into the new run:

- `../templates/PUBLIC_TRIAL_BRIEF_TEMPLATE.md`
- `../templates/RUN_MONITOR_TEMPLATE.md`
- `../templates/COMMAND_DISPATCH_TEMPLATE.md`
- `../templates/SEND_READY_PROMPT_TEMPLATE.md`
- `../templates/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- `../templates/SUBMISSION_PACKET_TEMPLATE.md`
- `../templates/FINAL_HANDOFF_TEMPLATE.md`
- `../templates/GAME_JUDGING_SCORECARD_TEMPLATE.md`
- `../templates/KIT_RETROSPECTIVE_TEMPLATE.md`

Add these when the run needs them:

- `../templates/00_INDEX_TEMPLATE.md`
- `../templates/INTERFACE_CONTRACT_FREEZE_TEMPLATE.md`
- `../templates/VERIFICATION_RECORD_TEMPLATE.md`
- `../templates/LANGUAGE_AND_ONBOARDING_CHECKLIST_TEMPLATE.md`

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

## Next Docs

- Live execution: [guides/runbook.md](guides/runbook.md)
- Preflight check: [guides/bootstrap-checklist.md](guides/bootstrap-checklist.md)
- Japanese onboarding: [ja/getting-started.md](ja/getting-started.md)
- Standalone release prep: [maintenance/publishing-checklist.md](maintenance/publishing-checklist.md)

