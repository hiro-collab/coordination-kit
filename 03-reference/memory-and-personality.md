# Memory And Personality

Use this when you want stable behavior without contaminating task-local state.

For a user, this file answers: "What should stay stable across runs, and what should stay disposable inside the current run?"

English comes first in this file. A Japanese mirror appears later in the same document.

Default starting point:

- start with `WORKING_MEMORY`
- add `PERSONALITY` only if you need stable behavior across sessions or across multiple runs

Rule of thumb:

- write `PERSONALITY` only for behavior you want to reuse later
- write `WORKING_MEMORY` for facts and reasoning that matter only in the current run
- if you are unsure, default to `WORKING_MEMORY`
- never let scratch notes turn into long-term policy by accident

## Durable And Disposable Layers

Use the smallest durable layer that fits the job.

- `CONSTITUTION`: hard guardrails that should change rarely
- `PERSONALITY`: stable style and default decision posture
- `BELIEFS`: selected cross-task beliefs that help many runs
- `TEAM_PROFILE`: team-local overlay when one team repeatedly works a certain way
- playbooks or skills: reusable but conditional methods
- `WORKING_MEMORY`: run-local facts, current intent, and intermediate reasoning
- logs and retrospectives: episodes of what happened this time

If you need a promotion workflow for durable carry-forward, open [profile-promotion.md](profile-promotion.md).

## Purpose

This model separates:

- Personality: persistent and reusable
- Working Memory: task-specific and disposable

This separation keeps behavior stable while allowing task-level adaptation.

## Personality

Use a `PERSONALITY` file when a node should keep persistent behavior policy across sessions.

Personality should contain stable items such as:

- default priorities
- default reporting style
- review posture
- individual bias or emphasis

Personality must not become a task log.

Keep reusable methods out of personality. If the content is really a step-by-step workflow, move it to a playbook instead.

Stable beliefs that outgrow one node's local style should move to `BELIEFS` or `TEAM_PROFILE`, not stay buried in a single personality file.

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

`Intentions` belong here when they are specific to the current run. Do not carry them forward by default.

## Strict Separation Rule

- Personality must not learn from working memory automatically.
- Working memory must not silently modify personality.
- Only explicit external review and update may change personality.

Here, `automatic learning` means behavior policy is not rewritten just because a task happened, a run finished, or a working-memory note was added.

When something seems worth keeping, send it to a candidate review step first instead of updating durable files directly.

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

## Japanese

このファイルは、安定した behavior を保ちつつ、今回の task の事情で durable profile を汚さないための基準です。

短い原則は次の通りです。

- 迷ったら `WORKING_MEMORY`
- 強い guardrail は `CONSTITUTION`
- 安定した style や posture は `PERSONALITY`
- 選別済みの durable belief は `BELIEFS` か `TEAM_PROFILE`
- 条件付きの手順は playbook
- 今回だけの `I` は `WORKING_MEMORY` にしか置かない

## Durable と Disposable の分け方

- `CONSTITUTION`: 変えにくい guardrail
- `PERSONALITY`: 安定した style や判断姿勢
- `BELIEFS`: 複数 run に効く selected belief
- `TEAM_PROFILE`: ある team にだけ効く overlay
- playbook / skill: 再利用できるが条件付きの方法
- `WORKING_MEMORY`: 今回の fact、intent、途中 reasoning
- log / retrospective: 今回何が起きたかという episode

durable carry-forward の判断手順が必要なら [profile-promotion.md](profile-promotion.md) を見てください。

## Personality

`PERSONALITY` は、session をまたいで残したい style や default posture のために使います。

ここに入れるもの:

- default priority
- reporting style
- review posture
- bias や emphasis

ここに入れないもの:

- task log
- 今回だけの intent
- step-by-step workflow

workflow なら playbook に寄せてください。複数 run で使える belief なら `BELIEFS` や `TEAM_PROFILE` の方が自然です。

## Working Memory

`WORKING_MEMORY` は session-local です。

ここに入れるもの:

- current task
- subtasks
- intermediate result
- current risk
- next action
- 今回だけの intent

通常は task や session ごとに入れ替えます。

## 厳格な分離

- `PERSONALITY` は `WORKING_MEMORY` から自動更新しない
- `WORKING_MEMORY` は `PERSONALITY` を勝手に書き換えない
- durable 変更は外部 review を経てから行う

「automatic learning をしない」とは、task が終わった、run が終わった、note が増えた、というだけで durable policy を更新しないという意味です。

残す価値がありそうな内容は、まず candidate review に送ります。
