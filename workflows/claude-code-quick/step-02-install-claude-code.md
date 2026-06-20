# Step 2: 安装 Claude Code

## 概述

前提条件检查通过后，安装 Claude Code。

## 安装方法

### 方法一：npx（推荐，无需全局安装）

```bash
npx @anthropic-ai/claude-code init
```

此方法会自动下载并运行 Claude Code 安装程序，按交互提示完成初始化。

### 方法二：npm 全局安装

```bash
npm install -g @anthropic-ai/claude-code
```

全局安装后可在任意目录直接执行 `claude` 命令。

### 方法三：直接运行（临时使用）

如果只是想试用：

```bash
npx @anthropic-ai/claude-code
```

## 配置 API Key

安装完成后，确保 `ANTHROPIC_API_KEY` 环境变量已正确设置：

```bash
export ANTHROPIC_API_KEY="your-api-key-here"
```

> **注意**：请将 `your-api-key-here` 替换为你的真实 API Key。切勿将真实 Key 写入日志或版本控制。

## 详细参考

- [Claude Code 安装指引](../../agents/claude-code/README.md) — 更多安装选项和常见问题
- [Shell 配置指引](../../config/shell/README.md) — 环境变量持久化配置

## 重要提醒

> **请与用户确认后再执行安装命令。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示安装计划（包含安装内容、预期变更、可能的风险），获得明确批准后方可执行。
