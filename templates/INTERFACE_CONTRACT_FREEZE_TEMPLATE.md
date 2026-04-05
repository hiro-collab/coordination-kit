# Interface Contract Freeze Template

Use this when two or more implementation lanes share a boundary and that boundary must stop drifting.

- Owner:
- Readers:

```text
[<team>] interface contract freeze

Checkpoint:
- <first integrated build|midpoint|post-cut|other>

Boundary:
- <for example: simulation -> scene>

Authoritative Files:
- <file path>

Owner Of This Boundary:
- <node>

Readers:
- <node or role>

Frozen Fields Or Calls:
- <field or function>

Restart / Reset Behavior:
- <how restart or reset is expected to work>

Known Gaps:
- <gap>

Do Not Change Without Explicit Recall:
- <what must not drift further>

Next Verification Step:
- <who verifies this and when>
```
