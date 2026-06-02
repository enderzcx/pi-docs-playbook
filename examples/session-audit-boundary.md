# Example: Map Session Trace To Application Audit

```md
I am confused about pi sessions.

If pi already stores session JSONL, do I still need my own application audit log or workflow records?

Use this repo as your pi documentation reference. Read the relevant source files first, then explain:

- what pi session files capture
- what compaction and branch summaries do
- why session trace is not the same as domain audit
- what my application should persist separately
- which source files you used
```

Expected reading path:

- `usage/task-reading-matrix.md`
- `source/packages/coding-agent/docs/session-format.md`
- `source/packages/coding-agent/docs/sessions.md`
- `source/packages/coding-agent/docs/compaction.md`
- `source/packages/agent/docs/durable-harness.md`
