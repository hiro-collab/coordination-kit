# Coordination Kit

Reusable coordination prompts, templates, and operating rules for a hierarchical multi-agent model centered on `Commander -> Arms -> Shoulder / Elbow / Fingers`.

This repository is process-first. It helps teams run visible, auditable multi-agent execution without relying on hidden coordination state.

The default concept is generic:

- Commander coordinates across one or more Arms.
- Each Arm may use a Shoulder, an optional Elbow, and one or more Fingers.
- Node names are identifiers, not fixed roles.

If an arm uses five finger lanes, the standard local names are `Thumb`, `Indy`, `Middy`, `Ringy`, and `Pinky`. Use compact node IDs such as `A.Thumb`, `A.Middy`, and `B.Shoulder`.

The structure is intentionally stage-based: at every directory level, the first file to read is `README.md` in that directory.

## Start Here

- English onboarding: [01-start-here/README.md](01-start-here/README.md)
- 日本語案内: [01-start-here/README.ja.md](01-start-here/README.ja.md)
- Generic runbook: [02-run-a-trial/README.md](02-run-a-trial/README.md)
- Topology and naming: [03-reference/agent-topology.md](03-reference/agent-topology.md)
- Memory and personality: [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md)

## Read In Order

1. [01-start-here/README.md](01-start-here/README.md)
2. [03-reference/agent-topology.md](03-reference/agent-topology.md)
3. [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md)
4. [02-run-a-trial/README.md](02-run-a-trial/README.md)
5. [prompts/README.md](prompts/README.md)
6. [templates/README.md](templates/README.md)
7. [04-maintainers/README.md](04-maintainers/README.md) if you maintain or publish the kit

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
- `03-reference/` holds the generic topology, memory model, stable rules, and lessons learned.
- `04-maintainers/` is for release and publishing work.
- `prompts/` contains startup prompts for Commander and active Shoulder threads.
- `templates/` contains reusable coordination files grouped by run phase.

## Recommended Use Order

1. Read [01-start-here/README.md](01-start-here/README.md).
2. If needed, share [01-start-here/README.ja.md](01-start-here/README.ja.md) with Japanese-speaking operators or judges.
3. Fix the generic topology with [03-reference/agent-topology.md](03-reference/agent-topology.md).
4. Confirm memory separation with [03-reference/memory-and-personality.md](03-reference/memory-and-personality.md).
5. Choose workspace isolation with [01-start-here/workspace-isolation.md](01-start-here/workspace-isolation.md).
6. Operate the run with [02-run-a-trial/README.md](02-run-a-trial/README.md).
7. Copy prompts and templates from [prompts/README.md](prompts/README.md) and [templates/README.md](templates/README.md) into your run workspace.
8. Review [03-reference/lessons-learned.md](03-reference/lessons-learned.md) after each trial and update the kit after judging is complete.

## Core Rules

- Higher-level nodes decompose and integrate; lower-level nodes execute.
- Roles are not fixed by Arm or Finger name.
- Keep reusable kit files separate from run-specific writable files.
- Treat file creation as storage, not instruction delivery.
- Keep persistent personality separate from task-specific working memory.
- Do not auto-update personality from working memory.
- Use visible artifacts for handoff, verification, and sign-off.
- Keep judge-facing and player-facing language aligned to the run's primary human language.
- After midpoint or the first integrated build, redistribute work visibly instead of letting everything collapse back to one operator.
- Use compact node IDs when lower nodes are active, for example `A.Thumb`, `A.Indy`, `A.Middy`, `A.Ringy`, and `A.Pinky`.

## Standalone Repository Notes

If you publish this kit as its own repository:

1. Keep this directory as the repository root.
2. Keep run-specific artifacts outside this repository.
3. Review [04-maintainers/publishing-checklist.md](04-maintainers/publishing-checklist.md) before release.
