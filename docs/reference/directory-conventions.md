# Directory Conventions

Use this to keep coordination files flexible without losing track of who should read them.

Related docs:

- [Getting Started](../getting-started.md)
- [Runbook](../guides/runbook.md)

## Responsibility Split

- `assets/coordination-kit/`
  - reusable templates, prompts, and policy
  - should not hold run-specific working files
- `trial-ops/`
  - run-specific global operations files
  - shared between Commander, user, and any team that needs global visibility
- `trial-runs/team-*/`
  - team-specific working files, code, handoff, and retrospective
  - should not be treated as global reference by the competing team unless explicitly allowed

## File Metadata

For human-facing markdown that may create ambiguity, add these lines near the top:

```text
- Owner:
- Readers:
```

This is most useful for:

- shared ops files
- handoff files
- integration notes
- retrospectives
- documents that many people may assume someone else is reading

## Index Files

If a directory is likely to grow during the run, create `00_INDEX.md`.

Use it to record:

- what belongs in this directory
- which files are most important
- what order to read them in

Do not use `00_INDEX.md` as a hard cap on file creation. Its job is navigation, not restriction.

## Dispatch Rule

Writing a file is not the same thing as dispatching work.

If a node must read a file and act on it:

1. write or update the file
2. send an explicit message to the responsible thread
3. name the file
4. state the required action
5. if needed, state the deadline

If a human intermediary must forward the message:

1. provide the full send-ready prompt body
2. do not rely on "please read the file I mentioned" as the only forwarding instruction

## Human Language Rule

Set one primary human language for the run.

This language should be used for:

- judge-facing summaries
- player-facing onboarding and rule explanation
- any file the user is expected to read directly during the run
