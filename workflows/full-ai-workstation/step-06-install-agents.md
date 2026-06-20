# Step 6: 安装 AI Agents

## 概述

安装 AI 编码 Agent。根据用户需求安装 Claude Code 和/或 Codex CLI。

## 安装选项

### 安装 Claude Code

需先确保 Node.js 18+ 已安装（Step 3），然后安装 Claude Code：

```bash
# 方法一：npx（推荐）
npx @anthropic-ai/claude-code init

# 方法二：npm 全局安装
npm install -g @anthropic-ai/claude-code
```

详细安装步骤请参考 [Claude Code 安装指引](../../agents/claude-code/README.md)。

### 安装 Codex CLI

```bash
npm install -g @openai/codex
```

详细安装步骤请参考 [Codex CLI 安装指引](../../agents/codex-cli/README.md)。

### 安装 Aider（可选，通过 pip）

```bash
pip install aider-chat
```

详细安装步骤请参考 [Aider 安装指引](../../agents/aider/README.md)。

## 详细参考

- [Claude Code 安装指引](../../agents/claude-code/README.md)
- [Codex CLI 安装指引](../../agents/codex-cli/README.md)
- [Aider 安装指引](../../agents/aider/README.md)
- [Node.js 安装指引](../../runtime/node-js/README.md)

## 重要提醒

> **请与用户确认后再执行安装命令。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示安装计划（包含安装内容、预期变更、可能的风险），获得明确批准后方可执行。

AI 应主动询问用户需要安装哪些 Agent，而非自行决定。
