# Reference

Use this folder after you already understand the front-door use case and need the stable rules behind the kit.

For a user, this folder answers questions like:

- "What lane structure am I asking the AI to create?"
- "Which file is the source of truth?"
- "What is stable policy and what is disposable run memory?"

English comes first in this file. A Japanese mirror appears later in the same document.

## Open This Folder When

- the quick-start flow already makes sense, but you want the stable rules
- you need to settle a naming, topology, or authority dispute
- you want to understand why the kit separates protocol, state, and policy

## Read In This Order

1. [agent-topology.md](agent-topology.md)
2. [coordination-primitives.md](coordination-primitives.md)
3. [memory-and-personality.md](memory-and-personality.md)
4. [directory-conventions.md](directory-conventions.md)
5. [lessons-learned.md](lessons-learned.md)

## Which File Answers Which Question

- `agent-topology.md`: "What stable lane structure and naming system should this run use?"
- `coordination-primitives.md`: "How does work move, where is visible truth stored, and who decides?"
- `memory-and-personality.md`: "What should stay stable across runs, and what should stay disposable?"
- `directory-conventions.md`: "Where should these files live, and who is supposed to read them?"
- `lessons-learned.md`: "What operating rules have already been learned from real runs?"

## Related Docs

- [Start Here](../01-start-here/README.md)
- [Reference Use Case](../01-start-here/reference-use-case.md)
- [Runbook](../02-runbook/README.md)
- [Templates](../templates/README.md)

## Japanese

このフォルダは、入口のユースケースを読んだあとに、この kit の固定ルールを確認したいときに開くための索引です。

ユーザー目線では、たとえば次の疑問に答えるために使います。

- 「AI にどんな lane 構造を作らせる前提なのか」
- 「どのファイルが source of truth なのか」
- 「何が stable policy で、何が run ごとの disposable memory なのか」

## このフォルダを開くタイミング

- quick-start の流れは分かったが、固定ルールを確認したい
- naming、topology、authority で迷いが出た
- protocol / state / policy をどう分けるのか確かめたい

## 読む順番

1. [agent-topology.md](agent-topology.md)
2. [coordination-primitives.md](coordination-primitives.md)
3. [memory-and-personality.md](memory-and-personality.md)
4. [directory-conventions.md](directory-conventions.md)
5. [lessons-learned.md](lessons-learned.md)

## どの疑問ならどのファイルか

- `agent-topology.md`: 「どの lane 構造と naming system を前提にするか」
- `coordination-primitives.md`: 「仕事がどう動き、visible truth がどこにあり、誰が決めるか」
- `memory-and-personality.md`: 「何を run をまたいで残し、何を task ごとに捨てるか」
- `directory-conventions.md`: 「ファイルをどこに置き、誰に読ませるか」
- `lessons-learned.md`: 「実運用から何を固定ルールとして学んだか」

## 関連ドキュメント

- [Start Here](../01-start-here/README.md)
- [Reference Use Case](../01-start-here/reference-use-case.md)
- [Runbook](../02-runbook/README.md)
- [Templates](../templates/README.md)
