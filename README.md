# pi-markdown

Local Markdown mirror and reading map for [`earendil-works/pi`](https://github.com/earendil-works/pi).

This repo exists so Pronto agent design can cite stable source files without depending on rendered `pi.dev` pages.

## Source

- Upstream repo: [`earendil-works/pi`](https://github.com/earendil-works/pi)
- Snapshot commit: [`f429ddb`](https://github.com/earendil-works/pi/tree/f429ddb)
- Snapshot date: 2026-06-01
- Local source clone used for import: `/tmp/pi-docs-read`

## Layout

- [`source/`](source/) mirrors upstream documentation-related Markdown files using original paths.
- [`catalog/`](catalog/) groups those files by how we read them for Pronto design.

The `source/` folder intentionally preserves upstream paths. Do not edit files under `source/` by hand unless you are intentionally patching the imported snapshot.

## Categories

- [Official coding-agent docs](catalog/official-coding-agent-docs.md)
- [Core runtime and harness docs](catalog/core-runtime-and-harness.md)
- [Examples and reusable patterns](catalog/examples-and-patterns.md)
- [Upstream prompts and skills](catalog/upstream-prompts-and-skills.md)
- [Validation fixtures and changelogs](catalog/validation-fixtures-and-changelogs.md)

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

## Pronto Reading Priority

1. `source/packages/coding-agent/docs/extensions.md`
2. `source/packages/coding-agent/docs/sdk.md`
3. `source/packages/coding-agent/docs/session-format.md`
4. `source/packages/coding-agent/docs/compaction.md`
5. `source/packages/coding-agent/docs/rpc.md`
6. `source/packages/agent/docs/agent-harness.md`
7. `source/packages/agent/docs/durable-harness.md`
8. `source/packages/agent/docs/hooks.md`
9. `source/packages/agent/docs/observability.md`

Main design reminder: pi session JSONL is agent trace, not Pronto business audit truth.
