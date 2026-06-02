# pi-markdown

Local Markdown mirror, documentation navigator, and agent-readable reading map for [`earendil-works/pi`](https://github.com/earendil-works/pi).

This repo exists so humans and coding agents can learn how to read pi's documentation before designing agent applications on top of pi.

It is not a pi tutorial. It is a documentation harness: a structured way to tell Codex, Claude, or another coding agent which pi docs to inspect for a given development question.

## Source

- Upstream repo: [`earendil-works/pi`](https://github.com/earendil-works/pi)
- Snapshot commit: [`f429ddb`](https://github.com/earendil-works/pi/tree/f429ddb)
- Snapshot date: 2026-06-01
- Local source clone used for import: `/tmp/pi-docs-read`

## Layout

- [`AGENTS.md`](AGENTS.md) gives coding agents the rules for using this repo.
- [`PROMPT.md`](PROMPT.md) is a copy-paste prompt for handing this repo to an agent.
- [`source/`](source/) mirrors upstream documentation-related Markdown files using original paths.
- [`catalog/`](catalog/) groups those files by topic and development use case.
- [`usage/`](usage/) explains how to use this repo as a reference library while designing agents on top of pi.
- [`examples/`](examples/) contains example questions you can ask an agent using this repo.
- [`skill-draft/`](skill-draft/) is a non-installable seed for a future skill. It captures the shape of a skill without claiming the lessons are stable yet.

The `source/` folder intentionally preserves upstream paths. Do not edit files under `source/` by hand unless you are intentionally patching the imported snapshot.

## Categories

- [Official coding-agent docs](catalog/official-coding-agent-docs.md)
- [Core runtime and harness docs](catalog/core-runtime-and-harness.md)
- [Examples and reusable patterns](catalog/examples-and-patterns.md)
- [Upstream prompts and skills](catalog/upstream-prompts-and-skills.md)
- [Validation fixtures and changelogs](catalog/validation-fixtures-and-changelogs.md)

## How To Use This Repo

Start with [usage/how-to-use-this-repo.md](usage/how-to-use-this-repo.md).

If you are a human:

- Open [PROMPT.md](PROMPT.md).
- Give this repo to your coding agent.
- Ask one of the questions in [examples/](examples/).

If you are an agent:

- Read [AGENTS.md](AGENTS.md) first.
- Read [usage/task-reading-matrix.md](usage/task-reading-matrix.md) before answering pi design questions.
- Use `source/` for exact upstream wording and line-level source checks.
- Use `catalog/` when you know the topic but not the upstream file.
- Use `skill-draft/` only as a parking lot for future pi-based agent development lessons. It is not an installable skill yet.

## Update Procedure

```bash
git clone --depth 1 https://github.com/earendil-works/pi.git /tmp/pi-docs-read
cd /Users/sunny/Work/CODEX/pi-markdown
rsync -a --prune-empty-dirs \
  --include='*/' \
  --include='*.md' \
  --include='*.mdx' \
  --include='packages/coding-agent/docs/docs.json' \
  --include='packages/coding-agent/docs/images/***' \
  --exclude='*' \
  /tmp/pi-docs-read/ source/
```

After updating, refresh this README commit hash and the catalog links if the upstream commit changes.

## Reading Priority For Agent App Development

1. `source/packages/coding-agent/docs/extensions.md`
2. `source/packages/coding-agent/docs/sdk.md`
3. `source/packages/coding-agent/docs/session-format.md`
4. `source/packages/coding-agent/docs/compaction.md`
5. `source/packages/coding-agent/docs/rpc.md`
6. `source/packages/agent/docs/agent-harness.md`
7. `source/packages/agent/docs/durable-harness.md`
8. `source/packages/agent/docs/hooks.md`
9. `source/packages/agent/docs/observability.md`

Main design reminder: pi session JSONL is agent trace, not your application's domain audit truth.
