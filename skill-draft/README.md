# Skill Draft: Pi Agent Application Design

This folder is a seed for a future skill.

It is intentionally not installable yet:

- no `SKILL.md`
- no frontmatter
- no trigger description

Reason: this repo is still a documentation reference. The repeatable workflow should become a skill only after enough concrete implementation patterns have been validated.

## Future Skill Goal

Help an agent design or review application modules built on top of pi by:

- selecting the right pi docs to read
- separating pi runtime trace from application domain truth
- designing mutation tools with approval, idempotency, validation, and application audit/event-log boundaries
- choosing SDK/RPC/extension topology
- checking compaction, session replacement, and tool parallelism risks

## Draft Inputs

When this becomes a real skill, the user should provide:

- target application module
- intended pi integration surface: SDK, extension, RPC, or CLI
- whether tools mutate business data
- expected approval/HITL behavior
- required evidence: application audit/event log, workflow/process record, tests, replay, UI confirmation, or logs

## Draft Output

The future skill should produce:

- source files read from this repo's `source/`
- application design boundary
- required application-owned contracts
- risks and footguns
- implementation checklist
- verification checklist

## Promotion Gate

Do not promote this to an actual skill until:

- at least one domain mutation tool has been implemented against pi
- at least one replay/golden trace exists
- approval/HITL behavior has been tested in the selected runtime mode
- session/process/audit mapping has been validated in code
- the repo has been refreshed against latest pi upstream
