# Agent Topology

Use this as the generic concept document for the kit.

For a user, this file answers one question: "If I ask AI to work in parallel, what stable lane structure am I asking it to create?"

Default starting point:

- one `Commander`
- one or two Arms
- no `Elbow` until one Arm actually needs another coordination layer

Start small:

- one `Commander`
- one or two `Arm` lanes
- one `Shoulder` inside each active Arm
- `Elbow` only when one Arm needs another coordination layer
- `Fingers` only for concrete parallel tasks

If you cannot explain why a second Arm exists, you probably do not need it yet.

## Purpose

This project uses a hierarchical multi-agent coordination model.

The structure is inspired by a body metaphor:
higher-level nodes control lower-level nodes as execution units.

This is a coordination model, not a literal anatomy.

## Topology

- Commander: top-level coordinator
- Arms: parallel work units such as `A`, `B`, `C`, `D`
- Each Arm may contain:
  - Shoulder: direction and control
  - Elbow: optional decomposition layer
  - Fingers: execution slots

## Hierarchy Shape

Do not read this as a flat sequence like `Commander -> Arms -> Shoulder -> Elbow -> Fingers`.

The intended shape is:

```text
Commander
  Arm A
    Shoulder
      Elbow (optional)
        Thumb / Indy / Middy / Ringy / Pinky
  Arm B
    Shoulder
      Fingers...
```

This means:

- Commander owns the overall mission.
- Each Arm is one parallel team lane under Commander.
- Shoulder, Elbow, and Fingers belong inside a specific Arm.
- Elbow is optional, and Shoulder may directly control Fingers.
- `A.Thumb` and `B.Thumb` are different nodes because they belong to different Arms.

You can think of Arms as team units or squad lanes under a single Commander.

## Core Principles

### Roles Are Not Fixed

- Arms do not have fixed roles.
- Fingers do not have fixed roles.
- Any node may perform research, implementation, validation, integration, or other work.

Structure is fixed. Meaning is dynamic.

### Delegation Model

Higher-level nodes such as Commander, Shoulder, and Elbow:

- decompose tasks
- assign work
- integrate results

Lower-level nodes such as Arms and Fingers:

- execute assigned tasks
- avoid global decisions unless instructed

### Parallel Execution

- Decompose work into independent subtasks when possible.
- Assign subtasks across Arms or Fingers.
- Run in parallel when it reduces coordination cost or time risk.
- Merge results explicitly after execution.

### Hierarchical Communication

Preferred flow:

- Commander ⇄ Shoulder
- Shoulder ⇄ Elbow when Elbow exists
- Elbow or Shoulder ⇄ Fingers

Avoid unnecessary lateral communication.

## Naming Conventions

Arms:

- `A`, `B`, `C`, `D`

For read-aloud names, many runs treat these as call-sign style team names such as:

- `A` -> `Alpha`
- `B` -> `Blabo`
- `C` -> `Charlie`
- `D` -> `Delta`

Project-specific team names are also acceptable as long as the compact IDs stay stable in files.

Finger local names:

- `Thumb`
- `Indy`
- `Middy`
- `Ringy`
- `Pinky`

Names are identifiers, not roles.

## Identification Format

Compact identifiers:

- `A.Thumb`
- `A.Middy`
- `B.Shoulder`
- `C.Elbow`

Human-readable examples:

- `Arm A Shoulder reports`
- `Message from Arm B Thumb`

## Structural Flexibility

- Some Arms may not have Elbow.
- Some Arms may have multiple Elbows.
- Shoulder may directly control Fingers.
- Finger count is often 5, but it may vary.

Common simplified shape without Elbow:

```text
Commander
  Arm A
    Shoulder
      Thumb / Indy / Middy / Ringy / Pinky
```

## Execution Model

Typical flow:

1. Commander receives task.
2. Commander assigns work to one or more Arms.
3. Shoulder defines direction.
4. Elbow, if present, decomposes further.
5. Fingers execute subtasks in parallel.
6. An upper layer integrates results.
7. Commander produces final output.

## Status Reporting

Always include node identity.

Examples:

- `[A.Shoulder] received task`
- `[A.Middy] processing`
- `[A.Ringy] validation complete`
- `[A.Thumb] consolidating results`
- `[Commander] final output ready`

## Completion Criteria

A task is complete only when:

- output is produced
- results are consistent
- assumptions are stated
- unresolved issues are listed

## Key Rule

Higher-level nodes decompose tasks, use lower-level nodes as parallel execution units, and integrate the results.
