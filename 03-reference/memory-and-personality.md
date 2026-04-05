# Memory And Personality

Use this when you want stable behavior without contaminating task-local state.

## Purpose

This model separates:

- Personality: persistent and reusable
- Working Memory: task-specific and disposable

This separation keeps behavior stable while allowing task-level adaptation.

## Personality

Use a `PERSONALITY` file when a node should keep persistent behavior policy across sessions.

Personality should contain stable items such as:

- beliefs
- default priorities
- default intentions
- individual bias

Personality must not become a task log.

## Working Memory

Use a `WORKING_MEMORY` file for session-local context.

Working memory should contain:

- current task
- subtasks
- intermediate results
- constraints
- current risks
- next actions

Working memory should be reset or replaced between tasks or sessions.

## Strict Separation Rule

- Personality must not learn from working memory automatically.
- Working memory must not silently modify personality.
- Only explicit external review and update may change personality.

Here, `automatic learning` means behavior policy is not rewritten just because a task happened, a run finished, or a working-memory note was added.

## Modes

Mode labels are optional task emphasis, not fixed agent classes.

Common examples are:

- `Explore`
- `Verify`
- `Integrate`

These are reference labels, not a required closed set.

## Control Policy

Commander should not overwrite personality directly.

Commander may instead apply:

- task assignment
- mode instruction
- priority pressure
- reallocation

This keeps behavior dynamic while preserving the stable core.

## Design Principles

- personality is stable
- behavior is dynamic
- roles are fluid
- memory is isolated
- traceability is required
