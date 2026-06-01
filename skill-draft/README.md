# Skill Draft: Pronto Pi Agent Design

This folder is a seed for a future skill.

It is intentionally not installable yet:

- no `SKILL.md`
- no frontmatter
- no trigger description

Reason: we are still using pi docs as reference material while designing Pronto. The repeatable workflow should become a skill only after Pronto has validated enough concrete patterns.

## Future Skill Goal

Help an agent design or review Pronto modules built on top of pi by:

- selecting the right pi docs to read
- separating pi runtime trace from Pronto business truth
- designing mutation tools with approval, idempotency, validation, and EventLog boundaries
- choosing SDK/RPC/extension topology
- checking compaction, session replacement, and tool parallelism risks

## Draft Inputs

When this becomes a real skill, the user should provide:

- target Pronto module
- intended pi integration surface: SDK, extension, RPC, or CLI
- whether tools mutate business data
- expected approval/HITL behavior
- required evidence: EventLog, ProcessInstance, tests, replay, UI confirmation, or logs

## Draft Output

The future skill should produce:

- source files read from `pi-markdown/source`
- Pronto design boundary
- required Pronto-owned contracts
- risks and footguns
- implementation checklist
- verification checklist

## Promotion Gate

Do not promote this to an actual skill until:

- at least one Pronto mutation tool has been implemented against pi
- at least one replay/golden trace exists
- approval/HITL behavior has been tested in the selected runtime mode
- session/process/audit mapping has been validated in code
- the repo has been refreshed against latest pi upstream
