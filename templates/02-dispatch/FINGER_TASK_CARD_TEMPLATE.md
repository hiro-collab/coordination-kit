# Finger Task Card Template

```text
Task ID: <A-01>
Node: <A.Thumb|A.Indy|A.Middy|A.Ringy|A.Pinky or other node id>
Mode: <mode label; examples: Explore|Verify|Integrate>

Mission:
<one-paragraph mission slice>

Read First:
- <project spec, or project README / mission brief>
- <shared note>
- <integration note>
- <working memory file>
- <log file>
- <other dependency>

Owned Scope:
- <files or modules>

Required Output:
- <artifact or result>

Required Output Checklist:
- <required line or artifact>
- <required line or artifact>
- any missing item means incomplete

Completion Evidence:
- <live output, visible file path, verification record, or other evidence>

Recovery Owner:
- <A.Shoulder|Commander|other>

Done Definition:
- <observable completion condition>
- all required checklist items above are visible
- visible node files reflect assumptions, outputs, blockers, and completion state

Constraints:
- do not change global scope
- node names are identifiers, not fixed specializations
- state assumptions explicitly
- expose uncertainty instead of hiding it
- escalate blockers early
- update `WORKING_MEMORY.<node>.md` at task start and completion
- update `LOG.<node>.md` with decisions and meaningful actions
- hidden agent state is non-authoritative unless echoed into visible files or status

Report Format:
[<node id>] status
Task:
Assumptions:
Done:
Blocked:
Next:
```
