# Git Usage

Use this guide when deciding how `coordination-kit` should live relative to an existing project repository.

English comes first in this file. A Japanese mirror appears later in the same document.

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

## Japanese

`coordination-kit` を既存の project repository に対してどこへ置くか決めるときは、この案内を使ってください。

## 推奨パターン

### 推奨: project repo の外に sibling として置く

これがいちばん安全な既定です。

```text
workspace/
  coordination-kit/
  your-project/
```

これを勧める理由:

- project の中に nested Git repository を作らずに済む
- kit を embedded repo として誤って stage する事故を避けやすい
- kit の更新や差し替えを project から独立して行いやすい
- project 側は必要な prompts や templates だけを取り込める

kit を主に reference material として使うなら、この配置が向いています。

### project 内で revision を固定したい場合: Git submodule

project の中で versioned reference として置きたいなら、submodule を使います。

```bash
git submodule add <repo-url> assets/coordination-kit
git submodule update --init --recursive
```

この方法が向いている場面:

- project が特定の kit revision を追跡したい
- team が submodule workflow に慣れている
- run の大半で kit を read-only reference として扱いたい

### シンプルな vendor copy

upstream tracking が不要なら、`.git` history を含めずに directory contents だけをコピーします。

この方法が向いている場面:

- project が local snapshot だけ欲しい
- upstream synchronization が重要ではない
- project 内の Git complexity を最小にしたい

## 避けたいパターン

意図的に nested repository を作り、その挙動を理解しているのでない限り、すでに Git 管理されている project directory の中で plain `git clone` を実行するのは避けてください。

危険な例:

```text
your-project/
  .git/
  coordination-kit/
    .git/
```

危険な理由:

- 親 repo の `git status` や `git add` が直感に反する動きをしやすい
- 通常ファイルではなく gitlink として nested repo を stage してしまうことがある
- 他の collaborator に意図した中身が渡らないことがある
- partial commit の事故が起きやすくなる

## 推奨まとめ

私たちの推奨は次の順です。

1. まずは `coordination-kit` を project repo の外に sibling repository として置く。
2. project repo の中に置く必要があるなら、Git submodule を使う。
3. update tracking が不要なら、nested `.git` を含めずに files をコピーする。

## 関連ドキュメント

- [Installation](README.md)
- [Workspace Isolation](workspace-isolation.md)
- [Runbook](../02-runbook/README.md)
