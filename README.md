# pi-docs-playbook

一个给人和 coding agent 用的 [`earendil-works/pi`](https://github.com/earendil-works/pi) 文档导航器。

它不是 pi 教程，也不是 pi 的 fork。

它更像一个 **documentation harness / docs navigator**：把 pi 的 Markdown 文档镜像下来，重新分类，并告诉 Codex、Claude、Cursor 或 Claude Code 在不同开发问题下应该读哪些文档。

核心目标很简单：

> 在让 AI 基于 pi 写 agent 之前，先让它把 pi 文档读对。

## 来源

- 上游仓库：[`earendil-works/pi`](https://github.com/earendil-works/pi)
- 当前镜像 commit：[`f429ddb`](https://github.com/earendil-works/pi/tree/f429ddb)
- 镜像日期：2026-06-01

## 这个 repo 解决什么问题

pi 文档不是没有，而是密度很高。

如果你直接把 pi repo 扔给 coding agent，它很容易：

- 凭记忆猜 pi 的行为
- 漏读关键文档
- 把 SDK、RPC、extension、session、compaction 混在一起
- 分不清 “pi 已经提供什么” 和 “你的应用必须自己设计什么”

所以这个 repo 做的事情不是替代官方文档，而是给官方文档加一层可导航的阅读路线。

## 目录结构

- [`AGENTS.md`](AGENTS.md)：给 coding agent 的使用规则。Agent 进入这个 repo 后应该先读它。
- [`PROMPT.md`](PROMPT.md)：可以直接复制给 Codex / Claude / Cursor 的提示词。
- [`source/`](source/)：原样镜像上游 pi 文档相关 Markdown 文件，保留原始路径。
- [`catalog/`](catalog/)：按主题和用途整理的文档索引。
- [`usage/`](usage/)：说明如何把这个 repo 当成 pi 文档参考库使用。
- [`examples/`](examples/)：可以直接问 agent 的示例问题。
- [`skill-draft/`](skill-draft/)：未来 skill 的草案，不是可安装 skill。

`source/` 目录刻意保留上游路径，方便精确引用。除非你明确要更新镜像，否则不要手动修改 `source/` 里的文件。

## 文档分类

- [Official coding-agent docs](catalog/official-coding-agent-docs.md)
- [Core runtime and harness docs](catalog/core-runtime-and-harness.md)
- [Examples and reusable patterns](catalog/examples-and-patterns.md)
- [Upstream prompts and skills](catalog/upstream-prompts-and-skills.md)
- [Validation fixtures and changelogs](catalog/validation-fixtures-and-changelogs.md)

## 怎么用

先读：

- [usage/how-to-use-this-repo.md](usage/how-to-use-this-repo.md)
- [usage/task-reading-matrix.md](usage/task-reading-matrix.md)

如果你是人类使用者：

1. 打开 [PROMPT.md](PROMPT.md)
2. 把这个 repo 交给你的 coding agent
3. 从 [examples/](examples/) 里挑一个问题开始问

如果你是 coding agent：

1. 先读 [AGENTS.md](AGENTS.md)
2. 再读 [usage/task-reading-matrix.md](usage/task-reading-matrix.md)
3. 根据用户问题判断任务类型
4. 只读取相关的 `source/` 文件
5. 回答时引用本地 `source/...` 路径
6. 不要把 `skill-draft/` 当成正式规范

## 典型问题

你可以这样问你的 agent：

- “我要基于 pi 做一个应用，SDK 和 RPC 应该选哪个？”
- “我要写一个会修改业务数据的 tool wrapper，应该先读哪些 pi docs？”
- “我想写一个 pi extension 拦截危险 tool call，怎么开始？”
- “pi session JSONL 已经记录了 trace，我还需要自己的 application audit log 吗？”
- “这个 repo 未来怎么整理成一个真正的 skill？”

对应模板在 [examples/](examples/)。

## 更新镜像

```bash
git clone --depth 1 https://github.com/earendil-works/pi.git /tmp/pi-docs-read
cd pi-docs-playbook
rsync -a --prune-empty-dirs \
  --include='*/' \
  --include='*.md' \
  --include='*.mdx' \
  --include='packages/coding-agent/docs/docs.json' \
  --include='packages/coding-agent/docs/images/***' \
  --exclude='*' \
  /tmp/pi-docs-read/ source/
```

更新后记得刷新 README 里的 commit hash，以及 catalog 里的链接。

## 推荐阅读顺序

如果你想基于 pi 开发 agent application，优先读：

1. `source/packages/coding-agent/docs/extensions.md`
2. `source/packages/coding-agent/docs/sdk.md`
3. `source/packages/coding-agent/docs/session-format.md`
4. `source/packages/coding-agent/docs/compaction.md`
5. `source/packages/coding-agent/docs/rpc.md`
6. `source/packages/agent/docs/agent-harness.md`
7. `source/packages/agent/docs/durable-harness.md`
8. `source/packages/agent/docs/hooks.md`
9. `source/packages/agent/docs/observability.md`

## 设计提醒

pi session JSONL 是 agent trace，不是你的 application domain audit truth。

pi 可以帮你处理 agent loop、tool calling、session、extension、RPC、TUI 等底层能力。

但业务状态机、审批、幂等、审计、异常补偿、domain rules，仍然必须由你的应用自己设计。

这也是为什么需要这个 repo：让 agent 先读对文档，再开始设计你的 harness。
