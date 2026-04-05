# Finger Task Card Template

```text
Node: <node id>
Mode: <Explore|Verify|Integrate or mixed emphasis>

Mission:
<one-paragraph mission slice>

Read First:
- <project spec>
- <shared note>
- <integration note>
- <working memory file>
- <log file>
- <other dependency>

Owned Scope:
- <files or modules>

Required Output:
- <artifact or result>

Done Definition:
- <observable completion condition>
- visible node files reflect assumptions, outputs, blockers, and completion state

Constraints:
- do not change global scope
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
