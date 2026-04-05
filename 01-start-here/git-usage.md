# Git Usage

Use this guide when deciding how `coordination-kit` should live relative to an existing project repository.

## Recommended Patterns

### Recommended: Keep The Kit Outside The Project Repo

This is the safest default.

```text
workspace/
  coordination-kit/
  your-project/
```

Why this is recommended:

- no nested Git repository inside the project
- no risk of accidentally staging the kit as an embedded repo
- easier to update or replace the kit independently
- the project can copy only the prompts and templates it actually needs

Use this when the kit is mainly reference material.

### Recommended When The Project Must Pin A Revision: Git Submodule

If the project needs a versioned in-repo reference, use a submodule.

```bash
git submodule add <repo-url> assets/coordination-kit
git submodule update --init --recursive
```

Use this when:

- the project must track a specific kit revision
- the team is comfortable with submodule workflow
- the kit should stay read-only during most runs

### Simple Vendor Copy

If you do not need upstream tracking, copy the directory contents without its `.git` history.

Use this when:

- the project wants a local snapshot
- upstream synchronization is not important
- you want the least Git complexity inside the project

## Pattern To Avoid

Avoid running a plain `git clone` inside an already versioned project directory unless you intentionally want a nested repository and understand the consequences.

Example of the risky pattern:

```text
your-project/
  .git/
  coordination-kit/
    .git/
```

Why this is risky:

- parent `git status` and `git add` can behave in surprising ways
- the project may stage the nested repo as a gitlink instead of ordinary files
- other collaborators may not receive what you expected
- accidental partial commits become more likely

## Recommendation Summary

This is what we recommend:

1. Prefer keeping `coordination-kit` as a sibling repository outside the project repo.
2. If it must live inside the project repo, prefer a Git submodule.
3. If you do not need update tracking, copy the files without the nested `.git`.

## Related Docs

- [Installation](README.md)
- [Workspace Isolation](workspace-isolation.md)
- [Runbook](../02-runbook/README.md)
