# Coordination Kit

Reusable coordination prompts, templates, and operating rules for the `Commander -> A.Shoulder -> fingers` model.

This repository is process-first. It helps teams run visible, auditable multi-thread or multi-agent execution without relying on hidden context.

## Start Here

- New to the kit: [docs/getting-started.md](docs/getting-started.md)
- Japanese quick guide: [docs/ja/getting-started.md](docs/ja/getting-started.md)
- Live trial operations: [docs/guides/runbook.md](docs/guides/runbook.md)
- File and directory rules: [docs/reference/directory-conventions.md](docs/reference/directory-conventions.md)

## Repository Layout

```text
coordination-kit/
  docs/
  prompts/
  templates/
  CHANGELOG.md
  LICENSE
  README.md
```

- `docs/` explains setup, live operation, conventions, lessons learned, and publishing.
- `prompts/` contains startup prompts for Commander and A.Shoulder.
- `templates/` contains reusable coordination files to copy into a real run.

## Recommended Use Order

1. Read [docs/getting-started.md](docs/getting-started.md).
2. Choose workspace isolation with [docs/guides/workspace-isolation.md](docs/guides/workspace-isolation.md).
3. Adopt directory responsibilities with [docs/reference/directory-conventions.md](docs/reference/directory-conventions.md).
4. Copy the required files from `prompts/` and `templates/` into your run workspace.
5. Operate the run with [docs/guides/runbook.md](docs/guides/runbook.md).
6. Review [docs/reference/lessons-learned.md](docs/reference/lessons-learned.md) after each trial and update the kit after judging is complete.

## Core Rules

- Keep reusable kit files separate from run-specific writable files.
- Treat file creation as storage, not instruction delivery.
- Use visible artifacts for handoff, verification, and sign-off.
- Keep judge-facing and player-facing language aligned to the run's primary human language.
- After midpoint or the first integrated build, redistribute work visibly instead of letting everything collapse back to one operator.

## Documentation Map

See [docs/README.md](docs/README.md) for the full document index.

## Standalone Repository Notes

If you publish this kit as its own repository:

1. Keep this directory as the repository root.
2. Keep run-specific artifacts outside this repository.
3. Review [docs/maintenance/publishing-checklist.md](docs/maintenance/publishing-checklist.md) before release.
