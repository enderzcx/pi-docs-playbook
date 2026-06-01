# How To Use This Repo

This repo is a reference library for designing Pronto agents on top of pi.

It is not a fork of pi, not an implementation repo, and not yet a skill. Treat it as a pinned upstream documentation snapshot plus our reading map.

## Working Modes

### 1. Exact Source Check

Use this when the question is "what does pi officially support?"

Read from `source/` only. Preserve upstream paths in citations.

Examples:

- Need exact extension hook behavior: read `source/packages/coding-agent/docs/extensions.md`.
- Need exact RPC protocol behavior: read `source/packages/coding-agent/docs/rpc.md`.
- Need exact session entry shape: read `source/packages/coding-agent/docs/session-format.md`.

### 2. Design Mapping

Use this when the question is "how should Pronto use pi?"

Start from `usage/task-reading-matrix.md`, then jump to the relevant `catalog/` page. After reading, write conclusions in Pronto docs, not inside `source/`.

Examples:

- Mapping pi session to Pronto `ProcessInstance`.
- Designing a Pronto mutation tool wrapper.
- Choosing embedded SDK vs RPC.
- Deciding how approvals work in CLI/RPC/UI contexts.

### 3. Lesson Capture

Use this when Pronto work produces a repeatable lesson.

Do not edit upstream `source/`. Add notes under `skill-draft/notes/` or update the draft checklist. Later, after enough lessons stabilize, promote them into a real skill.

## File Ownership

- `source/`: upstream mirror. Update only by re-importing from `earendil-works/pi`.
- `catalog/`: local index. Safe to edit as our reading map improves.
- `usage/`: local usage docs. Safe to edit as Pronto's needs become clearer.
- `skill-draft/`: future skill seed. Safe to edit, but keep it explicitly non-installable for now.

## Citation Rule

When using pi as evidence in Pronto design docs:

1. Cite the local `source/` path for stable offline work.
2. Include the upstream commit hash from `README.md`.
3. If the claim could drift, verify against latest upstream before implementation.

Example:

```md
Source: pi `f429ddb`, `source/packages/coding-agent/docs/extensions.md`
```

## What Not To Do

- Do not copy upstream docs into Pronto design docs wholesale.
- Do not treat pi session JSONL as Pronto audit truth.
- Do not turn draft notes into binding engineering rules before we have validated them in Pronto.
- Do not mutate `source/` manually and forget it is no longer a faithful snapshot.
