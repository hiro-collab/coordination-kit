# Agent Topology

Use this as the generic concept document for the kit.

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
