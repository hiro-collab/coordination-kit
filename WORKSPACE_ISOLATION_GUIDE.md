# Workspace Isolation Guide

As of 2026-04-04, `C:\Users\kawai\dev\works\codex_team_test_B` is not a git repository. `git worktree` cannot be used here until git is initialized in this directory and a baseline commit exists.

## Default Recommendation

For the first trial, use separate team directories inside the current project root:

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

## When To Introduce Git

Initialize git in this directory only if you want:

- branch history for each trial
- repeatable diffs between team outputs
- worktree-based isolation instead of plain directories

Minimum safe sequence:

1. run `git init` in `C:\Users\kawai\dev\works\codex_team_test_B`
2. commit the baseline kit and project files
3. create branches for the two trial teams
4. create worktrees under `.\worktrees\team-a` and `.\worktrees\team-b`

## Worktree Rules

- never create worktrees above `C:\Users\kawai\dev\works\codex_team_test_B`
- one team gets one worktree and one writable root
- do not let teams share mutable files during the active run
- update the coordination kit after the trial, not inside both team worktrees mid-run

## Decision Rule

- first trial: separate directories are enough
- later trials: introduce git and worktrees only if auditability or repeated reruns justify the extra setup
