# Coordination Kit

Reusable coordination prompts, templates, and operating rules for the `Commander -> A.Shoulder -> Thumb / Inddy / Middy / Ringy / Pinky` model.

This repository is process-first. It helps teams run visible, auditable multi-thread or multi-agent execution without relying on hidden context.

The structure is intentionally stage-based: at every directory level, the first file to read is `README.md` in that directory.

## Start Here

- English onboarding: [01-start-here/README.md](01-start-here/README.md)
- 日本語案内: [01-start-here/README.ja.md](01-start-here/README.ja.md)
- Live trial operations: [02-run-a-trial/README.md](02-run-a-trial/README.md)
- Stable rules and lessons: [03-reference/README.md](03-reference/README.md)

## Read In Order

1. [01-start-here/README.md](01-start-here/README.md)
2. [02-run-a-trial/README.md](02-run-a-trial/README.md)
3. [03-reference/README.md](03-reference/README.md)
4. [prompts/README.md](prompts/README.md)
5. [templates/README.md](templates/README.md)
6. [04-maintainers/README.md](04-maintainers/README.md) if you maintain or publish the kit

## Repository Structure

```text
coordination-kit/
  01-start-here/
  02-run-a-trial/
  03-reference/
  04-maintainers/
  prompts/
  templates/
  CHANGELOG.md
  LICENSE
  README.md
```

- `01-start-here/` is for first-time adoption and workspace setup.
- `02-run-a-trial/` is for live execution.
- `03-reference/` holds stable operating rules and lessons learned.
- `04-maintainers/` is for release and publishing work.
- `prompts/` contains startup prompts for Commander and A.Shoulder.
- `templates/` contains reusable coordination files grouped by run phase.

## Recommended Use Order

1. Read [01-start-here/README.md](01-start-here/README.md).
2. If needed, share [01-start-here/README.ja.md](01-start-here/README.ja.md) with Japanese-speaking operators or judges.
3. Choose workspace isolation with [01-start-here/workspace-isolation.md](01-start-here/workspace-isolation.md).
4. Operate the run with [02-run-a-trial/README.md](02-run-a-trial/README.md).
5. Copy prompts and templates from [prompts/README.md](prompts/README.md) and [templates/README.md](templates/README.md) into your run workspace.
6. Review [03-reference/lessons-learned.md](03-reference/lessons-learned.md) after each trial and update the kit after judging is complete.

## Core Rules

- Keep reusable kit files separate from run-specific writable files.
- Treat file creation as storage, not instruction delivery.
- Use visible artifacts for handoff, verification, and sign-off.
- Keep judge-facing and player-facing language aligned to the run's primary human language.
- After midpoint or the first integrated build, redistribute work visibly instead of letting everything collapse back to one operator.
- Use explicit finger names when lower nodes are active: `Thumb`, `Inddy`, `Middy`, `Ringy`, and `Pinky`.

## Standalone Repository Notes

If you publish this kit as its own repository:

1. Keep this directory as the repository root.
2. Keep run-specific artifacts outside this repository.
3. Review [04-maintainers/publishing-checklist.md](04-maintainers/publishing-checklist.md) before release.
