# Step 3: 安装 AI Agent

## 概述

安装 AI 编码 Agent。根据用户需求选择 Claude Code 或 Codex CLI（或两者都安装）。

## 安装选项

### 选项 A：安装 Claude Code

需先安装 Node.js 18+，然后安装 Claude Code：

```bash
# 安装 Node.js（如已安装可跳过）
sudo apt install -y nodejs npm

# 安装 Claude Code
npx @anthropic-ai/claude-code init
```

详细安装步骤请参考 [Claude Code 安装指引](../../agents/claude-code/README.md)。

### 选项 B：安装 Codex CLI

需先安装 Node.js 18+，然后安装 Codex CLI：

```bash
# 安装 Node.js（如已安装可跳过）
sudo apt install -y nodejs npm

# 全局安装 Codex CLI
npm install -g @openai/codex
```

详细安装步骤请参考 [Codex CLI 安装指引](../../agents/codex-cli/README.md)。

### 选项 C：安装 Aider

通过 pip 安装（Python 3.10+ 已就绪）：

```bash
pip install aider-chat
```

或使用 uv（更快的 Python 包管理器）：

```bash
pip install uv
uv pip install aider-chat
```

详细安装步骤请参考 [Aider 安装指引](../../agents/aider/README.md)。

## 详细参考

- [Claude Code 安装指引](../../agents/claude-code/README.md)
- [Codex CLI 安装指引](../../agents/codex-cli/README.md)
- [Aider 安装指引](../../agents/aider/README.md)
- [Node.js 安装指引](../../runtime/node-js/README.md)

## 重要提醒

> **请与用户确认后再执行安装命令。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示安装计划（包含安装内容、预期变更、可能的风险），获得明确批准后方可执行。

AI 应主动询问用户需要安装哪个 Agent，而非自行决定。
