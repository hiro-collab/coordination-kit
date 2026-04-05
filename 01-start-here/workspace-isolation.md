# Workspace Isolation Guide

Use this guide before any team starts writing files.

## Default Recommendation

For most first runs, use separate arm directories inside the current project root:

```text
run-workspaces/
  arm-a/
  arm-b/
```

This is the safest starting point because:

- it does not require git setup
- it does not write above the current project root
- it makes each Arm's writable area explicit
- it keeps `assets/coordination-kit` available as a shared read-only reference

## When To Introduce Git Worktrees

Use git worktrees only if you need:

- branch history for each run
- repeatable diffs between Arm outputs
- isolation that follows repository branches rather than plain directories

## Minimum Safe Worktree Sequence

1. Initialize git in the project root if the project is not already a repository.
2. Commit the baseline kit and project files.
3. Create one branch per active Arm or execution lane.
4. Create worktrees under `./worktrees/arm-a` and `./worktrees/arm-b`.

## Worktree Rules

- never create worktrees above the current project root
- one active Arm gets one worktree and one writable root
- do not let Arms share mutable files during the active run
- update the coordination kit after the run, not inside multiple active Arm worktrees mid-run

## Decision Rule

- first run: separate directories are enough
- later runs: introduce git and worktrees only if auditability or repeated reruns justify the extra setup

## Related Docs

- [Getting Started](README.md)
- [Git Usage](git-usage.md)
- [Runbook](../02-runbook/README.md)
- [Directory Conventions](../03-reference/directory-conventions.md)
