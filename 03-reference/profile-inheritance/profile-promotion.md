# Profile Promotion

Use this when a run taught you something useful and you need to decide whether it should stay disposable, become a playbook, or become durable team behavior.

For a user, this file answers: "What is safe to carry forward across runs, and what should stay local to this job?"

English comes first in this file. A Japanese mirror appears later in the same document.

## Quick Answer

- Put always-on cross-task rules in the base profile.
- Put team-local defaults in a team profile, not in the global base.
- Put reusable but conditional methods in playbooks, not in personality.
- Keep current-task facts, blockers, and workarounds inside run files only.
- Do not promote anything straight from working memory into durable profile files.

## Recommended Layers

```text
run-ops/
  profiles/
    base/
      CONSTITUTION.md
      PERSONALITY.md
      BELIEFS.md
    teams/
      A/
        TEAM_PROFILE.md
    candidates/
      <run-id>/
        PROFILE_CANDIDATES.md
        PROFILE_PROMOTION_REVIEW.md
  playbooks/
    verification.md
    escalation.md
```

These names are recommended, not magical. The important part is the separation.

- `CONSTITUTION.md`: hard guardrails that should be difficult to change
- `PERSONALITY.md`: durable default style and decision posture
- `BELIEFS.md`: selected cross-task beliefs that help many runs
- `TEAM_PROFILE.md`: team-local overlay for one stable team or lane family
- `playbooks/`: reusable but conditional methods
- `PROFILE_CANDIDATES.md`: parking lot for possible promotions after a run

## BDI Mapping

- `D`: `CONSTITUTION.md` and `PERSONALITY.md`
- selected `B`: `BELIEFS.md` and `TEAM_PROFILE.md`
- `I`: `WORKING_MEMORY.*.md` only

Do not carry `I` forward. If a belief is not selected and reviewed, do not carry it forward either.

## Promotion Rubric

### Promote To Base Profile

Use the base profile only for rules that are safe to keep always loaded.

Promote here when the item:

- helps across different task types
- is not tied to one repository, path, tool, or topology
- can be written as a short principle instead of a long procedure
- would still help on the next unrelated run
- has low risk if read in every run

Examples:

- claims of completion must include evidence
- simulated and live execution must be distinguished
- blockers should be escalated early

### Promote To Team Profile

Use a team profile when the pattern is useful for one stable team but should not become a global default.

Promote here when the item:

- helps one team repeatedly
- reflects that team's preferred reporting or collaboration style
- would be distracting or unnecessary for every other team

Examples:

- team Alpha writes status in three lines or fewer
- team Blabo prefers Japanese for direct operator updates

### Move To Playbook

Use a playbook when the content is a method, checklist, or triggered workflow.

Move here when the item:

- is step-based
- applies only when a certain situation appears
- would add noise if loaded on every run
- is really a reusable operating method, not a stable trait

Examples:

- shoulder spawn probe and recovery flow
- verification handoff checklist
- browser-game judging flow

### Keep Run-Only

Keep the item inside run files only when it is local to the current job.

Keep here when the item:

- mentions the current bug, path, owner, branch, or workaround
- depends on the current repository or sprint
- will likely be stale in the next run
- describes what happened this time rather than how to behave in general

Examples:

- Commander recovery was needed in this smoke test
- Arm B owns the auth bug in the current run
- use `../coordination-kit` for this repository layout

### Reject

Reject promotion when the item:

- has only worked once
- becomes harmful when always loaded
- is too long to stay readable
- is really a specific workaround disguised as a rule

## Anti-Overfit Safeguards

- Candidate first: write new ideas to `PROFILE_CANDIDATES.md` before any promotion.
- Two-run rule: prefer promotion only after the idea proved useful in at least two different runs.
- Negative case required: every promoted item should say when not to use it.
- No direct copy from working memory: summarize and review first.
- Keep base thin: if the base grows heavy, move specific items down to team profiles or playbooks.
- Review by PR: base changes should be reviewed like code changes.

## Review Questions

Before promotion, ask:

1. Will this still help on a different kind of task?
2. Is this a principle or just a procedure?
3. Would it be safe if always loaded?
4. Does it avoid project-specific paths, branches, and tools?
5. Can I state when not to use it?
6. Is this better as a playbook or team overlay?
7. Do I have evidence from more than one run?

## Git Governance

If you want Git-backed promotion:

- keep approved profile files on the protected main branch
- keep unreviewed ideas in candidate files or candidate branches
- require review for base-profile changes
- use CODEOWNERS for approved profile paths if the repository supports it

The important rule is simple: branches transport proposals, but reviewed files remain the durable source of truth.

## Japanese

このファイルは、run で得た学びを「今回だけのこと」に留めるのか、「再利用できる playbook」にするのか、「長く残す profile」にするのかを決めるときに使います。

短く言うと、次のように分けるのが安全です。

- 常時読ませても害が少ない cross-task rule は base profile
- ある team ではよく効くが全体既定にはしたくないものは team profile
- 条件付きの手順や checklist は playbook
- 今回の bug、path、owner、workaround は run-only
- 新しい学びはまず `PROFILE_CANDIDATES.md` に置き、いきなり durable file に入れない

## 推奨レイヤー

- `CONSTITUTION.md`: 変えにくい guardrail
- `PERSONALITY.md`: 安定した style や判断姿勢
- `BELIEFS.md`: 複数 run で役立つ selected belief
- `TEAM_PROFILE.md`: team ごとの overlay
- `playbooks/`: 再利用できるが常時適用したくない方法
- `PROFILE_CANDIDATES.md`: 昇格候補の一時置き場

## BDI 対応

- `D`: `CONSTITUTION.md` と `PERSONALITY.md`
- 選別済みの `B`: `BELIEFS.md` と `TEAM_PROFILE.md`
- `I`: `WORKING_MEMORY.*.md` のみ

`I` は引き継ぎません。選別されていない `B` も引き継がないのが原則です。

## 昇格の目安

### Base Profile に上げる

次のようなものだけに絞ります。

- 仕事の種類が変わっても効く
- 特定 repo、path、tool、topology に依存しない
- 長い手順ではなく短い原則として書ける
- 次の unrelated run でも助けになる
- 毎回読まれても害が少ない

例:

- 完了主張には evidence を付ける
- simulated と live を混同しない
- blocker は早めに escalate する

### Team Profile に上げる

ある team には効くが、全体既定にはしたくないものを置きます。

- その team では繰り返し効く
- team 固有の reporting style や collaboration style に近い
- 他 team ではノイズになりうる

### Playbook に移す

手順、checklist、条件付き workflow は playbook に送ります。

- step-based である
- 特定状況でだけ使う
- 常時ロードするとノイズになる
- stable trait ではなく reusable method である

### Run-Only に留める

今回だけの事情は durable profile に上げません。

- 今回の bug、path、owner、branch、workaround
- 現在 repo に依存する事情
- 次回には古くなりそうな内容
- 「今回は何が起きたか」の記録

### Reject する

- まだ 1 回しか効いていない
- 毎回読ませると邪魔
- 長すぎて読みづらい
- 実質的には局所 workaround

## 過学習を防ぐルール

- まず candidate に置く
- 2 種類以上の run で効いてから昇格を考える
- 「いつ使わないか」を必ず書く
- `WORKING_MEMORY` から直接 durable file に写さない
- base は薄く保つ
- base の変更は code change と同じように review する

## レビュー質問

1. 別種類の task でも効くか
2. これは手順ではなく原則か
3. 常時読ませても安全か
4. project 固有の path、branch、tool を含んでいないか
5. 使わない条件を書けるか
6. playbook や team overlay に置く方が自然ではないか
7. 2 回以上の evidence があるか

## Git 運用

Git で管理するなら、次が分かりやすいです。

- approved profile は保護された main に置く
- 未承認の案は candidate file か candidate branch に置く
- base profile の変更は review 必須にする
- 可能なら CODEOWNERS で approved path を保護する

要するに、branch は提案の運搬路であり、review 済み file が durable な正本です。
