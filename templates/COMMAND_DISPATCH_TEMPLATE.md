# Command Dispatch Template

Use this when a file has been written and a node must actually read it and act.

```text
Sender:

Recipient:

Read:
- <absolute or project-relative file path>

Action Required:
- <what to do>

Required Output:
- <what must be updated or returned>

Destination File:
- <where the required output must appear>

Deadline:
- <time or checkpoint>

Do Not Do:
- <scope guard>

Reply Format:
[<node>] status
Task:
Done:
Blocked:
Next:
```

Notes:

- Do not rely on "I wrote it in the file" as the only instruction.
- Name both the file and the action.
- If a human must forward this dispatch, also provide the exact message body they should paste.
