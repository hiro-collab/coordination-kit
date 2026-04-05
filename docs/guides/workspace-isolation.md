# Workspace Isolation

Use this guide before any team starts writing files.

## Default Recommendation

For most first trials, use separate team directories inside the current project root:

```text
trial-runs/
  team-a/
  team-b/
```

This is the safest starting point because:

- it does not require git setup
- it does not write above the current project root
- it makes each team's writable area explicit
- it keeps `assets/coordination-kit` available as a shared read-only reference

## When To Introduce Git Worktrees

Use git worktrees only if you need:

- branch history for each trial
- repeatable diffs between team outputs
- isolation that follows repository branches rather than plain directories

## Minimum Safe Worktree Sequence

1. Initialize git in the project root if the project is not already a repository.
2. Commit the baseline kit and project files.
3. Create one branch per trial team.
4. Create worktrees under `./worktrees/team-a` and `./worktrees/team-b`.

## Worktree Rules

- never create worktrees above the current project root
- one team gets one worktree and one writable root
- do not let teams share mutable files during the active run
- update the coordination kit after the trial, not inside multiple active team worktrees mid-run

## Decision Rule

- first trial: separate directories are enough
- later trials: introduce git and worktrees only if auditability or repeated reruns justify the extra setup

## Related Docs

- [Getting Started](../getting-started.md)
- [Runbook](runbook.md)
- [Directory Conventions](../reference/directory-conventions.md)
