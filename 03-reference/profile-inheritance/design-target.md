# Design Target

Use this file when you want to understand why `profile-inheritance` exists before reading the detailed rules.

For a user, this file answers: "What is this mechanism trying to preserve, and what is it deliberately refusing to preserve?"

English comes first in this file. A Japanese mirror appears later in the same document.

## One-Sentence Target

Keep the AI recognizable as the same long-term collaborator while refusing to drag task-local work history across runs.

## Problem Statement

In many AI workflows, two bad defaults compete:

- everything is forgotten, so the agent never feels like a continuous collaborator
- everything is carried forward, so stale task facts and accidental habits pollute future runs

This kit aims for a narrower middle:

- preserve durable personality and selected reviewed beliefs
- discard run-local memory, active intentions, and local workarounds

## What Should Carry Forward

These are the kinds of things this mechanism is meant to preserve, but only through explicit review:

- interaction style
- reporting style
- review posture
- risk posture
- stable preference in ambiguity or escalation
- selected cross-task beliefs that help in many runs

## What Should Not Carry Forward

These are the things the mechanism is designed to leave behind after a run:

- current task facts
- current branch, path, bug, owner, or workaround
- intermediate reasoning from this run
- task-local intentions
- one-off tricks that only helped in a specific repository state

## Why Git Is In The Loop

Git is not used here as "memory by accident."

It is used so that durable changes are:

- visible
- reviewable
- comparable
- reversible

Branches may carry proposals, but reviewed files remain the durable source of truth.

## Design Boundary

This mechanism is not trying to create a self-updating personality that silently learns from every run.

It is trying to create a reviewed, explicit, human-governed carry-forward path for:

- personality
- selected beliefs
- team-local overlays
- reusable playbooks when needed

## Open Questions

These questions are still intentionally open and should stay visible:

- What belongs in `PERSONALITY` versus `BELIEFS`?
- How "human-like" should a durable personality be?
- Which traits are helpful across many tasks, and which become noise?
- How much should be global versus team-local?
- What evidence threshold is enough before promotion?

## Reading Map

- Read [memory-and-personality.md](memory-and-personality.md) for the durable versus disposable split.
- Read [profile-promotion.md](profile-promotion.md) for the review and promotion path.

## Japanese

このファイルは、詳細ルールに入る前に、なぜ `profile-inheritance` という束が必要なのかを確認したいときに読むための note です。

利用者の言葉で言えば、このファイルが答える問いは次です。
「この仕組みは何を残したくて、何を意図的に残さないのか」

## 一文でいうと

AI を「同じ長期的な協働相手」として認識できる程度には保ちつつ、task-local な作業履歴は次の run に持ち込まないことを目指します。

## 問題設定

AI の運用では、悪い既定が 2 つあります。

- 何もかも忘れるので、継続的な協働相手としての感じが消える
- 何もかも引き継ぐので、古い task fact や偶発的な癖が次の run を汚す

この kit が目指すのは、その中間です。

- durable な personality と、review 済みの selected belief だけを残す
- run-local な memory、active intention、local workaround は捨てる

## 引き継ぎたいもの

この仕組みが保持対象として想定しているのは、次のようなものです。ただし、いずれも explicit review を通したものに限ります。

- 接し方の style
- 報告の style
- review posture
- risk posture
- 迷ったときの判断傾向や escalation の癖
- 複数 run で役立つ selected cross-task belief

## 引き継がないもの

この仕組みが run の後に捨てる前提なのは、次のようなものです。

- current task の fact
- current branch、path、bug、owner、workaround
- 今回の途中 reasoning
- task-local な intention
- 特定の repository 状態でしか効かなかった one-off のコツ

## なぜ Git を介在させるのか

ここでの Git は「いつの間にか残る記憶」のためではありません。

durable な変更を次の性質にするためです。

- visible
- reviewable
- comparable
- reversible

branch は提案を運ぶが、review 済み file を durable な正本にする、というのが基本方針です。

## 設計境界

この仕組みは、run を重ねるたびに personality が黙って自己更新されるような設計を目指していません。

目指しているのは、次を human-governed かつ explicit に carry-forward する経路です。

- personality
- selected belief
- team-local overlay
- 必要なら reusable playbook

## 未解決の問い

次の問いは、まだ意図的に open のまま残しておくべきものです。

- `PERSONALITY` と `BELIEFS` の境界はどこか
- durable personality は、どこまで human-like であるべきか
- 多くの task で有益な trait と、単なる noise になる trait をどう分けるか
- どこまでを global にし、どこからを team-local にするか
- promotion 前に必要な evidence の閾値をどう置くか

## Reading Map

- durable / disposable の分離は [memory-and-personality.md](memory-and-personality.md) を読む
- review と promotion の経路は [profile-promotion.md](profile-promotion.md) を読む
