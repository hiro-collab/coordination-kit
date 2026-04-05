# Templates

Copy these files into the active project workspace. If the run is competitive, that live workspace may also use trial-oriented directory names. Do not treat the kit copy as the live working area.

From the user side, this folder answers: "Which files should I ask the AI to create in the live workspace?"

Most human users do not need this folder until placement, writable boundaries, and the first run shape are already decided.

Read this folder in order:

1. [01-setup/README.md](01-setup/README.md)
2. [02-dispatch/README.md](02-dispatch/README.md)
3. [03-checkpoints/README.md](03-checkpoints/README.md)
4. [04-handoff/README.md](04-handoff/README.md)

## Japanese Note

フォルダ名がそのまま利用タイミングです。迷ったら、まず `01-setup/` から順に見てください。
多くの human user は、placement、writable boundary、最初の run shape が決まるまでこのフォルダを開かなくて構いません。
比較型 run でないなら、profile-specific な template は無理に使わなくて構いません。

## Rules

- Copy templates out into the run workspace.
- Only copy profile-specific templates when the run actually uses that profile.
- Keep the kit repository reusable and mostly read-only during live execution.
- Pair file creation with explicit dispatch when someone must read and act.

## Related Docs

- [Start Here](../01-start-here/README.md)
- [Runbook](../02-runbook/README.md)
- [AI / System Reference](../03-reference/README.md)
