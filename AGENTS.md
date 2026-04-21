# AGENTS.md

## Repository Role

This repository is a documentation-first coordination kit for visible, auditable multi-agent work.

It is not a workflow engine, distributed runtime, agent graph runtime, or live run workspace.

## Read Order

For orientation, read in this order:

1. `README.md`
2. `01-start-here/README.md`
3. `01-start-here/project-placement.md`
4. `02-runbook/README.md`
5. `03-reference/README.md` only when topology, authority, memory, or protocol rules need deeper review

At every directory level, prefer the local `README.md` as the entry point before opening deeper files.

## Working Boundaries

- Keep reusable kit source files in this repository.
- Do not create live run artifacts in this repository unless the task is explicitly to edit templates or examples.
- Live run files belong in the adopting project's `run-ops/` and `run-workspaces/` directories.
- If this kit is used from a sibling project, treat this repository as mostly read-only source material.
- Do not turn `coordination-kit` into an execution engine or scheduler.

## Change Guidelines

- Preserve the stage-based directory structure.
- Keep the front-door docs concise for human operators.
- Keep advanced rules in `03-reference/`, prompts in `prompts/`, and reusable live-run files in `templates/`.
- Do not fix roles by Arm or Finger name; names are identifiers.
- Keep persistent personality separate from task-specific working memory.
- Keep competitive browser-game trials as an optional profile, not the default concept.
- When editing bilingual front-door guidance, keep the English and Japanese sections aligned in meaning.
- Treat file creation as storage, not dispatch. If a node must act, the instruction must explicitly name the file and required action.

## Review Guidelines

When reviewing changes, look for:

- confusion between reusable kit files and run-specific writable files
- docs that imply this repository executes jobs or manages background workflows
- topology changes that flatten `Commander -> Arm -> Shoulder / Elbow / Fingers`
- role assumptions tied to names such as `Alpha`, `Thumb`, or `Pinky`
- missing updates to related README, prompt, template, or changelog files
- live-run artifacts accidentally committed into the kit
