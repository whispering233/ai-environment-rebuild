# Step 4: 配置环境

## 概述

配置 API Key、Shell 环境变量及其他必要配置。

## 配置项

### 1. 配置 API Key

根据安装的 Agent，设置对应的 API Key：

```bash
# Claude Code
export ANTHROPIC_API_KEY="your-api-key-here"

# Codex CLI
export OPENAI_API_KEY="your-api-key-here"
```

将 API Key 写入 shell 配置文件以持久生效：

```bash
echo 'export ANTHROPIC_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

> **注意**：请将 `your-api-key-here` 替换为真实 API Key。切勿将真实 Key 写入日志或版本控制。

### 2. 配置 Shell 环境

确保以下环境变量已正确设置：

- `PATH` 包含 Python、Node.js 的全局 bin 目录
- `EDITOR` 或 `VISUAL` 设置（可选）
- Shell 别名（可选）

详细配置指引请参考 [Shell 配置指引](../../config/shell/README.md)。

### 3. 配置 OpenCode（如果使用）

OpenCode 配置文件位于 `~/.opencode/`，请参考 [OpenCode 配置指引](../../config/opencode/README.md) 进行配置。

## 详细参考

- [Shell 配置指引](../../config/shell/README.md)
- [OpenCode 配置指引](../../config/opencode/README.md)
- [隐私保护规则](../../RULES.md) — API Key 的处理必须遵守隐私保护规则

## 重要提醒

> **请与用户确认后再执行配置变更。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示配置计划，获得明确批准后方可执行。
