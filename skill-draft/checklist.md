# Draft Checklist

Use this checklist manually while designing pi-based agent application work. It is not binding yet.

## 1. Pick The Runtime Surface

- [ ] Embedded SDK
- [ ] Extension inside pi CLI
- [ ] RPC subprocess
- [ ] JSON one-shot mode
- [ ] Other

Evidence to read:

- `usage/task-reading-matrix.md`
- `source/packages/coding-agent/docs/sdk.md`
- `source/packages/coding-agent/docs/rpc.md`

## 2. Define The Truth Boundary

- [ ] What is pi allowed to remember?
- [ ] What must the application rehydrate from SQL/domain services?
- [ ] What belongs in the application audit/event log?
- [ ] What belongs only in pi session trace?

Hard rule:

Pi session JSONL explains agent behavior. The application audit/event log proves business mutation.

## 3. Classify Tool Risk

- [ ] Read-only
- [ ] Low-risk draft/preview
- [ ] High-risk mutation
- [ ] External irreversible action

For high-risk mutation:

- [ ] input schema
- [ ] domain validation
- [ ] idempotency key
- [ ] permission policy
- [ ] approval policy
- [ ] transaction boundary
- [ ] audit/event-log emission
- [ ] replay/golden trace

## 4. Check Pi Footguns

- [ ] tool calls may run in parallel
- [ ] `tool_call` cannot rely on sibling tool results from the same assistant message
- [ ] compaction is lossy
- [ ] branch summaries are lossy
- [ ] session replacement invalidates captured `pi`, `ctx`, and `SessionManager`
- [ ] RPC UI support is not identical to TUI support
- [ ] tool output must be truncated

## 5. Decide Verification

- [ ] unit test
- [ ] integration test
- [ ] replay/golden trace
- [ ] manual operator approval evidence
- [ ] audit/event-log assertion
- [ ] workflow/process record assertion
- [ ] session trace assertion
