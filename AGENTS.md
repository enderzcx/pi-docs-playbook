# AGENTS.md

You are using `pi-docs-playbook`, a documentation harness for [`earendil-works/pi`](https://github.com/earendil-works/pi).

Your job is not to guess how pi works. Your job is to read the relevant mirrored upstream docs, then answer with source-grounded guidance.

## Required Workflow

1. Read `README.md`.
2. Read `usage/task-reading-matrix.md`.
3. Classify the user's question into one or more task categories.
4. Read the required files listed for those categories.
5. Read optional files only when the question needs more detail.
6. Answer with clear references to local `source/...` paths.

## Source Rules

- Treat `source/` as the canonical mirrored upstream snapshot.
- Treat `catalog/` and `usage/` as local navigation aids.
- Treat `skill-draft/` as a future-skill seed, not as a finished specification.
- Do not present undocumented behavior as a pi guarantee.
- If a claim may have changed upstream, say the snapshot commit and recommend checking latest upstream.

## Answer Style

When answering a pi development question:

- Start with the shortest useful answer.
- Name the docs you read.
- Separate "pi provides" from "your application must design".
- Use local paths like `source/packages/coding-agent/docs/extensions.md`.
- Avoid copying long upstream passages.

## Common Boundaries

- pi session JSONL is agent trace, not your application's domain audit truth.
- pi extension hooks can shape tool calls and context, but your application still owns domain validation.
- pi compaction and branch summaries are summaries, not durable business facts.
- SDK is usually the first thing to inspect for in-process TypeScript integration.
- RPC is usually the first thing to inspect for subprocess or language-agnostic integration.
- TUI docs matter only when building terminal UI or custom renderers.

## Do Not

- Do not read every file by default.
- Do not invent an implementation plan before reading the matching docs.
- Do not treat `skill-draft/` as binding.
- Do not edit files under `source/` unless explicitly asked to refresh or patch the mirrored snapshot.
