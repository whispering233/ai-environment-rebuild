# Agents — AI Agent 安装知识

每个 Agent 一个子目录，知识**自包含**（概述、安装目标、来源链接、配置、验证、更新、关键注意点），不引用其他目录的知识。

## Agent 一览

| Agent | 定位 | 依赖 | 文档 |
|-------|------|------|------|
| [Claude Code](./claude-code/README.md) | Anthropic 终端 AI 编码 | Node.js 18+ | `agents/claude-code/` |
| [Codex CLI](./codex-cli/README.md) | OpenAI 终端 AI 编码 | Node.js 18+ | `agents/codex-cli/` |
| [Aider](./aider/README.md) | 开源结对编程，多模型 | Python 3.10+、Git | `agents/aider/` |
| [OpenCode](./opencode/README.md) | 开源终端 AI 编码 | Node.js | `agents/opencode/` |
| [Pi](./pi/README.md) | 极简终端编码 harness，可扩展 | Node.js | `agents/pi/` |

## 定位说明

- 本目录属于**知识层**：只描述安装目标与关键经验，不决定执行顺序
- 执行顺序由 [workflows/](../workflows/README.md) 编排
- 详细安装步骤以各 Agent 的**来源链接**（官方文档）为准，LLM 拉取后自行判断执行
- 所有 Agent 均涉及 API Key，遵守 [commons/AGENTS.md](../commons/AGENTS.md) 拉取的全局规则中的隐私保护要求
