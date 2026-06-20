# Agents — AI Agent 安装知识

本子项目包含各主流 AI 编码 Agent 的安装要点、前提条件、注意事项。每个 Agent 一个子目录，列出独立的安装指引。

## Agent 一览

| Agent | 适用场景 | 依赖 | 安装方式 |
|-------|----------|------|----------|
| [Claude Code](./claude-code/README.md) | 通用 AI 编码、代码生成、重构 | Node.js 18+, Anthropic API Key | `npx` / `npm global` |
| [Codex CLI](./codex-cli/README.md) | OpenAI 生态 AI 编码 | Node.js 18+, OpenAI API Key | `npm install -g @openai/codex` |
| [Aider](./aider/README.md) | 开源 AI 结对编程、多模型支持 | Python 3.10+, Git, API Key | `pip install aider-chat` / `uv pip install aider-chat` |

## 知识层 vs 编排层

本目录属于**知识层**，只描述如何安装，不决定执行顺序。执行顺序由 [workflows/](../workflows/README.md) 中的工作流决定。

关于项目整体结构、知识层与编排层的分离规则，请参阅 [INDEX.md](../INDEX.md) 和 [RULES.md](../RULES.md)。

## 隐私说明

所有 Agent 安装均涉及 API Key 配置。请严格遵守 [RULES.md](../RULES.md) 中的隐私保护规则，切勿将真实 API Key 写入文件或对话日志。本目录中的所有文档均使用 `your-api-key-here` 等占位符代替真实值。
