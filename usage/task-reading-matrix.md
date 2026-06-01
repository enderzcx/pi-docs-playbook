# Task Reading Matrix

Use this matrix to decide which pi files to read for a specific pi-based agent application design question.

## Runtime Topology

Read when deciding embedded SDK vs RPC vs CLI usage.

Required:

- `source/packages/coding-agent/docs/sdk.md`
- `source/packages/coding-agent/docs/rpc.md`
- `source/packages/coding-agent/docs/json.md`
- `source/packages/coding-agent/docs/usage.md`

Optional:

- `source/packages/agent/README.md`
- `source/packages/agent/docs/agent-harness.md`
- `source/packages/coding-agent/examples/sdk/README.md`

Use for:

- Embedding pi in an application backend.
- Running pi as an isolated subprocess.
- Designing a custom UI/client around pi.

## Tool Wrapper Design

Read when designing high-risk domain tools such as inventory movement, order mutation, payment actions, or confirmation actions.

Required:

- `source/packages/coding-agent/docs/extensions.md`
- `source/packages/coding-agent/docs/sdk.md`
- `source/packages/agent/README.md`
- `source/packages/agent/docs/hooks.md`

Optional:

- `source/packages/coding-agent/examples/extensions/README.md`
- `source/packages/coding-agent/examples/extensions/plan-mode/README.md`
- `source/packages/coding-agent/test/suite/README.md`

Use for:

- app-specific tool wrapper design
- approval gates
- idempotency and validation boundaries
- tool result rendering
- tool parallelism and serialization risks

## Session, Process, And Audit Mapping

Read when mapping pi sessions to application workflow records, event logs, and replay.

Required:

- `source/packages/coding-agent/docs/session-format.md`
- `source/packages/coding-agent/docs/sessions.md`
- `source/packages/coding-agent/docs/compaction.md`
- `source/packages/agent/docs/durable-harness.md`

Optional:

- `source/packages/agent/docs/observability.md`
- `source/packages/agent/docs/agent-harness.md`

Use for:

- pi session ID vs application process/workflow ID.
- fork/clone/tree behavior.
- replay and explainability.
- distinguishing agent trace from business audit.

## Context Builder And Memory Policy

Read when deciding what facts may enter the model context.

Required:

- `source/packages/coding-agent/docs/compaction.md`
- `source/packages/coding-agent/docs/session-format.md`
- `source/packages/coding-agent/docs/extensions.md`

Optional:

- `source/packages/ai/README.md`
- `source/packages/agent/docs/observability.md`

Use for:

- SQL/domain rehydration.
- compacted context risk.
- tool output truncation.
- redaction and telemetry.

## Approval UX And Human In The Loop

Read when designing confirmation, review, and operator approval surfaces.

Required:

- `source/packages/coding-agent/docs/extensions.md`
- `source/packages/coding-agent/docs/rpc.md`
- `source/packages/coding-agent/docs/tui.md`

Optional:

- `source/packages/tui/README.md`
- `source/packages/coding-agent/examples/extensions/plan-mode/README.md`

Use for:

- CLI dialog behavior.
- RPC extension UI protocol.
- what degrades outside interactive TUI.
- future operator console behavior.

## Model And Provider Routing

Read when choosing providers, auth, custom provider hooks, or deployment routing.

Required:

- `source/packages/coding-agent/docs/providers.md`
- `source/packages/coding-agent/docs/models.md`
- `source/packages/coding-agent/docs/custom-provider.md`
- `source/packages/ai/README.md`

Optional:

- `source/.pi/skills/add-llm-provider.md`

Use for:

- provider auth.
- model compatibility knobs.
- custom streaming APIs.
- OpenAI/Anthropic routing differences.

## Skills, Prompts, And Packaging

Read when deciding whether your project should ship reusable instructions or installable pi packages.

Required:

- `source/packages/coding-agent/docs/skills.md`
- `source/packages/coding-agent/docs/prompt-templates.md`
- `source/packages/coding-agent/docs/packages.md`
- `source/packages/coding-agent/examples/extensions/dynamic-resources/SKILL.md`

Optional:

- `source/packages/coding-agent/test/fixtures/skills/valid-skill/SKILL.md`
- `source/packages/coding-agent/test/fixtures/skills/name-mismatch/SKILL.md`

Use for:

- future pi-based agent development skill.
- prompt template conventions.
- package distribution.
- skill validation edge cases.

## Terminal UX

Read only when building or debugging a terminal experience.

Required:

- `source/packages/coding-agent/docs/tui.md`
- `source/packages/tui/README.md`
- `source/packages/coding-agent/docs/keybindings.md`

Optional:

- `source/packages/coding-agent/docs/themes.md`
- `source/packages/coding-agent/docs/terminal-setup.md`
- `source/packages/coding-agent/docs/tmux.md`

Use for:

- custom renderers.
- keyboard handling.
- terminal compatibility.
- theme behavior.

## Upstream Drift Check

Read when updating this repo or validating whether old conclusions still hold.

Required:

- `source/packages/coding-agent/CHANGELOG.md`
- `source/packages/agent/CHANGELOG.md`
- `source/packages/ai/CHANGELOG.md`
- `source/packages/tui/CHANGELOG.md`

Optional:

- Latest upstream GitHub docs.

Use for:

- checking breaking changes.
- refreshing the snapshot.
- deciding whether a design claim is stale.
