# Prompt For Codex / Claude

Copy this prompt when giving `pi-docs-playbook` to a coding agent.

```md
I am building an agent application on top of pi.

Use this repo as your pi documentation reference.

First read:

- README.md
- AGENTS.md
- usage/task-reading-matrix.md

Then classify my question, read only the relevant mirrored upstream docs under source/, and answer with local source paths.

Do not guess pi behavior from memory.
Do not treat skill-draft/ as a finished skill.
Separate what pi provides from what my application must design itself.
```

## Short Version

```md
Use this repo as a pi docs navigator. Read README.md, AGENTS.md, and usage/task-reading-matrix.md first. Then inspect the relevant source/ files before answering.
```
