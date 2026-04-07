# Profile Inheritance

Use this folder when you need to decide how a node's stable personality should carry forward without dragging task-local memory across runs.

This folder groups the durable-profile rules that would otherwise be scattered across `03-reference/`.

English comes first in this file. A Japanese mirror appears later in the same document.

## Read In This Order

1. [design-target.md](design-target.md)
2. [memory-and-personality.md](memory-and-personality.md)
3. [profile-promotion.md](profile-promotion.md)

## Which File Answers Which Question

- `design-target.md`: "What is this mechanism trying to preserve, and what is it deliberately refusing to preserve?"
- `memory-and-personality.md`: "What should stay stable across runs, and what should stay disposable?"
- `profile-promotion.md`: "What is safe to carry forward, and what should stay local to this run?"

## Design Focus

- durable personality should stay reviewable and explicit
- task-local working memory should stay disposable
- reusable methods should move to playbooks instead of bloating personality
- Git branches may carry proposals, but reviewed files remain the durable source of truth

## Japanese

このフォルダは、node の安定した personality を run をまたいでどう引き継ぐか、そして task-local な memory をどう切り離すかを考えるときに開きます。

`03-reference/` の中で散りやすい durable-profile 関連の規則を、このサブディレクトリにまとめています。

## 読む順番

1. [design-target.md](design-target.md)
2. [memory-and-personality.md](memory-and-personality.md)
3. [profile-promotion.md](profile-promotion.md)

## どの疑問ならどのファイルか

- `design-target.md`: 「この仕組みは何を残したくて、何を意図的に残さないのか」
- `memory-and-personality.md`: 「何を run をまたいで残し、何を disposable にするか」
- `profile-promotion.md`: 「何を carry forward してよく、何を今回限りに留めるべきか」

## この束の主題

- durable な personality は review 可能で明示的に保つ
- task-local な working memory は disposable に保つ
- 再利用可能な方法は personality を肥大化させず playbook に逃がす
- Git branch は提案を運ぶが、review 済み file を durable な正本にする
