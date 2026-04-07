# Lessons Learned

- Owner: Commander / kit maintainer
- Readers: user, Commander, visible A.Shoulder threads, future operators

Use this as the maintainer-facing record of rules that survived real runs.

Most items below are generic carry-forward rules. Trial-only notes are kept in a separate section so they do not accidentally redefine the default model.

Read this after the core reference docs already make sense. This file is a retrospective layer, not the first explanation of the model.

English comes first in this file. A Japanese mirror appears later in the same document.

## Generic Lessons

### What Worked

- Separate writable workspaces kept active lanes isolated and avoided polluting unrelated directories.
- Shared templates made it easier to compare operating-model quality across runs.

### What Needed Improvement

- Writing a file was often mistaken for dispatching work; explicit thread-level commands were still required.
- Telling an operator "the prompt is in that file" was still too indirect; forwarders needed the actual send-ready body.
- The directory and markdown layout was flexible, but file ownership and readership were not obvious enough.
- Final handoff content became clear only late in the run and should have been standardized earlier.
- The issue in multi-node execution was not headcount by itself, but whether every node had clear work, visibility, and coordination.
- Teams needed a visible post-checkpoint redistribution step so completed or partially idle nodes could shift into verification, docs, localization, or handoff support.
- Teams needed visible interface-contract freeze notes when integration drifted.

### Rules To Carry Forward

- Use a visible A.Shoulder thread when the user needs to steer it directly.
- Treat writing a file and dispatching a task as separate steps; send an explicit message naming the file and required action.
- If a human operator must relay the instruction, give them the full send-ready prompt body in addition to any reference file.
- Create shared coordination files before finger spawning begins.
- Make file ownership explicit before collaborative execution starts.
- Add `Owner:` and `Readers:` to human-facing markdown where ambiguity would cause delays.
- Add `00_INDEX.md` in directories that may grow during a run so new files remain navigable.
- Treat hidden thread context as non-authoritative unless echoed into visible files or status.
- Freeze canonical contract files after the first integrated build or checkpoint when multiple lanes have started to drift.
- Write visible redistribution after checkpoint changes so every active node either has a new role or is explicitly released.
- Schedule phase-end reminders and escalations before required visible updates are late.
- Require final handoff to be submitted in a fixed visible format.
- Evaluate multi-node collaboration by contribution quality and coordination quality, not by assuming fewer nodes are automatically better.

### Generic Failure Checks

- A.Shoulder becomes only an advisor while Commander micro-manages fingers.
- Fingers complete code work without updating visible state.
- Shared assumptions change without `SHARED_NOTE.md` updates.
- A file is updated, but no responsible thread is explicitly told to read it and act.
- A send-ready prompt exists only as a file reference, so the human forwarder still has to reconstruct what to send.
- Handoff is treated as implicit rather than submitted in a fixed visible format.
- Some nodes remain idle because ownership, dependencies, or required inputs were not made explicit.
- Some nodes finish their first slice but are never recalled or reassigned after checkpoint changes.
- Shared boundaries drift, but no visible contract freeze names the authoritative file and owner.

## Competitive Browser-Game Trial Notes

These notes are useful when the run is explicitly a judged browser-game comparison. They are not the generic default.

- Visible `LIVE_STATUS_BOARD.md` updates made it possible to compare team progress without relying on hidden thread state.
- Time checkpoints such as plan lock, midpoint, feature freeze, and submission cutoff gave Commander clear intervention moments.
- Shared templates made it possible to collect both game-quality judgment and operating-model judgment from the same run.
- `midpoint playable` was too easy to interpret loosely; it should mean a demonstrable end-to-end live run.
- Judge-facing materials and first-play guidance needed stronger Japanese support.
- Teams needed a team-local submission packet before the final shared-board update so handoff content did not have to be reconstructed from scattered files.
- Teams also needed visible proof-of-play records when playable claims were disputed.
- Record game winner, operations winner, and overall result separately when those judgments diverge.
- Use the primary human language for judge-facing summaries and player-facing onboarding.

### Trial Failure Checks

- Midpoint is marked complete without a visible end-to-end run.
- The player can technically launch the build but cannot quickly find the rule explanation.
- A team claims playable progress, but there is no visible verification record showing what was actually tested.

## Pending Follow-Up

- Merge the forthcoming Team Alpha retrospective into these lessons once it is visible.
- Merge the forthcoming Team Blabo retrospective into these lessons once it is visible.
- Re-check whether the new dispatch, handoff, and directory rules cover the concrete failures the teams report.

## Reading Map

- Read [agent-topology.md](agent-topology.md) for the lane structure itself.
- Read [coordination-primitives.md](coordination-primitives.md) for protocol, state, and policy.
- Read [profile-inheritance/README.md](profile-inheritance/README.md) for durable personality and carry-forward rules.

## Japanese

- Owner: Commander / kit maintainer
- Readers: user, Commander, visible A.Shoulder threads, future operators

このファイルは、実運用を通って生き残ったルールを maintainer 視点で記録するためのものです。

下の大半は generic な carry-forward ルールです。trial 専用の note は別 section に分け、既定モデルを書き換えてしまわないようにしています。

このファイルは、core reference docs がすでに頭に入っている前提で読みます。最初にモデルを説明する文書ではなく、retrospective layer です。

## Generic Lessons

### うまくいったこと

- writable workspace を分けたことで、active lane を分離でき、無関係な directory を汚さずに済んだ。
- shared template により、run ごとの operating-model quality を比較しやすくなった。

### 改善が必要だったこと

- file を書くことが dispatch と誤認されがちで、明示的な thread-level command がなお必要だった。
- operator に「prompt はその file にある」と伝えるだけでは間接的すぎ、転送者には send-ready な本文が必要だった。
- directory と markdown の layout は柔軟だったが、file ownership と readership が十分には明示されていなかった。
- final handoff の内容は run のかなり後半になってから明確になり、もっと早く標準化すべきだった。
- multi-node execution の問題は頭数そのものではなく、各 node に clear な work、visibility、coordination があるかどうかだった。
- checkpoint 後に、完了済みまたは半待機状態の node を verification、docs、localization、handoff support に移せる visible な再配分 step が必要だった。
- integration drift が起きたときに、visible な interface-contract freeze note が必要だった。

### 引き継ぐべきルール

- user が直接 steering したいときは、visible な `A.Shoulder` thread を使う。
- file を書くことと task を dispatch することを分け、file 名と required action を明示した message を送る。
- human operator が relay する必要があるなら、reference file だけでなく send-ready な prompt 本文も渡す。
- finger spawn を始める前に、shared coordination file を作る。
- collaborative execution の前に、file ownership を明示する。
- 曖昧さで遅れが出そうな human-facing markdown には `Owner:` と `Readers:` を入れる。
- file が増えそうな directory には `00_INDEX.md` を入れて、後から見ても辿れるようにする。
- hidden thread context は、visible file や status に反映されない限り authoritative とみなさない。
- 複数 lane が drift し始めたら、最初の integrated build や checkpoint の後で canonical contract file を freeze する。
- checkpoint 後に visible な redistribution を書き、active な各 node に新しい役割があるか、明示的に release されている状態にする。
- required な visible update が遅れる前に、phase-end reminder と escalation を仕込む。
- final handoff は fixed visible format で提出させる。
- multi-node collaboration は、人数の多少ではなく contribution quality と coordination quality で評価する。

### Generic Failure Checks

- `A.Shoulder` が advisor に退き、`Commander` が fingers を micro-manage している。
- `Fingers` が code work を終えても visible state を更新しない。
- shared assumption が変わったのに `SHARED_NOTE.md` が更新されていない。
- file は更新されたが、誰がそれを読んで act するかが thread に明示されていない。
- send-ready prompt が file reference としてしか存在せず、human forwarder が結局 message を再構成する必要がある。
- handoff が fixed visible format で提出されず、暗黙のものとして扱われている。
- ownership、dependency、required input が明示されず、idle な node が出る。
- node が最初の slice を終えても、checkpoint 後に recall や reassignment がされない。
- shared boundary が drift しているのに、authoritative file と owner を示す visible contract freeze がない。

## Competitive Browser-Game Trial Notes

これらは、run が明示的に judged browser-game comparison であるときに有用な note です。generic default ではありません。

- visible な `LIVE_STATUS_BOARD.md` update により、hidden thread state に頼らず team progress を比較できた。
- plan lock、midpoint、feature freeze、submission cutoff のような time checkpoint により、`Commander` が介入すべき瞬間を持てた。
- shared template により、game quality の評価と operating-model の評価を同じ run から集められた。
- `midpoint playable` は解釈が緩すぎたので、visible な end-to-end live run を意味するよう定義すべきだった。
- judge-facing material と first-play guidance には、より強い日本語対応が必要だった。
- final shared-board update の前に team-local submission packet が必要で、そうしないと handoff 内容を scattered file から再構成する羽目になった。
- playable claim が争点になったときのために、visible proof-of-play record も必要だった。
- game winner、operations winner、overall result は判断が分かれうるので別々に記録すべきだった。
- judge-facing summary と player-facing onboarding には primary human language を使うべきだった。

### Trial Failure Checks

- visible な end-to-end run がないのに midpoint 完了としている。
- build 自体は起動できても、player が rule explanation をすぐ見つけられない。
- team が playable progress を主張しているのに、実際に何をテストしたかを示す visible verification record がない。

## Pending Follow-Up

- forthcoming な Team Alpha retrospective が visible になったら、ここへ統合する。
- forthcoming な Team Blabo retrospective が visible になったら、ここへ統合する。
- 新しい dispatch、handoff、directory ルールが、team の報告する具体的 failure を本当にカバーできているか再確認する。

## Reading Map

- lane structure 自体は [agent-topology.md](agent-topology.md) を読む。
- protocol、state、policy は [coordination-primitives.md](coordination-primitives.md) を読む。
- durable personality と carry-forward rule は [profile-inheritance/README.md](profile-inheritance/README.md) を読む。
