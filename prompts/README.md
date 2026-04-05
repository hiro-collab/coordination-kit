# Prompts

Use this folder when you are ready to start visible working threads.

From the user side, this is the folder you open when you want the AI system to start acting as `Commander` or as a visible `Shoulder`.

These prompts work best after the user has already named the exact kit path and exact writable project paths.

There is no default `ARM_THREAD_PROMPT.md` because an `Arm` is usually the lane identity. The default acting thread inside an Arm is `Shoulder`.

Read this folder in order:

1. `COMMANDER_THREAD_PROMPT.md`
2. `SHOULDER_THREAD_PROMPT.md`

## When To Use Each Prompt

- `COMMANDER_THREAD_PROMPT.md`: start here for the top-level coordination thread
- `SHOULDER_THREAD_PROMPT.md`: use when an Arm's Shoulder needs to be a visible thread or receive direct user instructions

## Standard Node IDs

Use compact IDs that preserve hierarchy, for example:

- `A.Shoulder`
- `A.Elbow`
- `A.Thumb`
- `A.Indy`
- `A.Middy`
- `A.Ringy`
- `A.Pinky`

If an Arm uses five finger lanes, the local finger names are `Thumb`, `Indy`, `Middy`, `Ringy`, and `Pinky`.

Names are identifiers, not fixed roles.

## Related Docs

- [Start Here](../01-start-here/README.md)
- [Agent Topology](../03-reference/agent-topology.md)
- [Memory and Personality](../03-reference/memory-and-personality.md)
- [Runbook](../02-runbook/README.md)
- [Templates](../templates/README.md)
