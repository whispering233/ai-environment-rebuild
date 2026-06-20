# Runtime — 语言运行时

本子项目包含各主流语言运行时的安装指引，涵盖版本管理工具和安装方式。

## 运行时一览

| 运行时 | 版本管理 | 安装方式 |
|--------|----------|----------|
| [Node.js](./node-js/README.md) | nvm/fnm | Node.js 22 LTS |
| [Python](./python/README.md) | pyenv/uv | Python 3.12 |
| [Go](./golang/README.md) | go install | Go 1.22 |

## 与 `agents/` 的关系

[agents/](../agents/README.md) 中多数 AI Agent（如 Claude Code、Codex CLI）依赖 Node.js 或 Python 运行时。建议在安装 Agent 之前先完成语言运行时的安装。

## 知识层说明

本目录属于**知识层**，只描述运行时安装方法，不决定执行顺序。执行顺序由 [workflows/](../workflows/README.md) 中的工作流决定。

关于项目整体结构、知识层与编排层的分离规则，请参阅 [INDEX.md](../INDEX.md) 和 [RULES.md](../RULES.md)。
