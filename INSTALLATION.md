# Installation

Use this when you want to bring `coordination-kit` into another workspace.

This kit is a documentation-and-templates repository. There is no package manager install step.

## Recommended Options

### Option 1: Copy The Directory

Use this when you want a local editable copy inside a project and do not need to track upstream updates automatically.

1. Copy `coordination-kit/` into your target workspace.
2. Keep it under a stable path such as:

```text
assets/coordination-kit/
```

3. Read `README.md`.
4. Follow `RUNBOOK.md` and `DIRECTORY_CONVENTIONS.md`.
5. Copy the needed templates into your active run workspace.

### Option 2: Clone As A Standalone Reference Repo

Use this when you want to keep the kit in its own repository and copy templates into working projects as needed.

```bash
git clone <repo-url> coordination-kit
```

Then:

1. Read `README.md`.
2. Read `RUNBOOK.md`.
3. Copy the needed files from `templates/` and `prompts/` into your target project.

### Option 3: Add As A Git Submodule

Use this when you want your project to reference a versioned copy of the kit and update it explicitly.

```bash
git submodule add <repo-url> assets/coordination-kit
git submodule update --init --recursive
```

Then:

1. Read `assets/coordination-kit/README.md`.
2. Keep run-specific files outside the kit directory.
3. Copy templates into `trial-ops/` and team workspaces instead of editing the kit during a live run.

## Minimum Files To Start A New Trial

Read first:

- `README.md`
- `RUNBOOK.md`
- `DIRECTORY_CONVENTIONS.md`
- `WORKSPACE_ISOLATION_GUIDE.md`

Usually copy these into the new run:

- `prompts/COMMANDER_THREAD_PROMPT.md`
- `prompts/SHOULDER_THREAD_PROMPT.md`
- `templates/PUBLIC_TRIAL_BRIEF_TEMPLATE.md`
- `templates/RUN_MONITOR_TEMPLATE.md`
- `templates/COMMAND_DISPATCH_TEMPLATE.md`
- `templates/SEND_READY_PROMPT_TEMPLATE.md`
- `templates/POST_CHECKPOINT_REDISTRIBUTION_TEMPLATE.md`
- `templates/SUBMISSION_PACKET_TEMPLATE.md`
- `templates/FINAL_HANDOFF_TEMPLATE.md`
- `templates/GAME_JUDGING_SCORECARD_TEMPLATE.md`
- `templates/KIT_RETROSPECTIVE_TEMPLATE.md`

Add these when the run needs them:

- `templates/00_INDEX_TEMPLATE.md`
- `templates/INTERFACE_CONTRACT_FREEZE_TEMPLATE.md`
- `templates/VERIFICATION_RECORD_TEMPLATE.md`
- `templates/LANGUAGE_AND_ONBOARDING_CHECKLIST_TEMPLATE.md`

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

Or, if the kit stays external:

```text
coordination-kit/
your-project/
  trial-ops/
  trial-runs/
```

## Update Policy

- Treat the kit as reusable source material.
- Keep run-specific files outside the kit.
- If you improve the kit during a trial, back it up first and push those changes later as a kit revision.

## Before Publishing Or Reusing Widely

- Read `PUBLISHING_CHECKLIST.md`.
- Add a license if the repository will be public.
- Make sure all references still make sense when `coordination-kit` is the repository root.

