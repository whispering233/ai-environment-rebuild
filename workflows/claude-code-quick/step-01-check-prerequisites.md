# Step 1: 检查前提条件

## 概述

在执行安装前，先确认当前环境是否满足 Claude Code 的安装前提条件。

## 检查项

### 1. 检查 Node.js 版本

运行以下命令检查 Node.js 是否已安装以及版本是否符合要求：

```bash
node --version
```

**期望输出**：`v18.x.x` 或更高版本（建议 v20 LTS）。

如果版本低于 18，请先升级 Node.js。升级指引请参考 [runtime/node-js/](../../runtime/node-js/README.md)。

### 2. 检查 npm

```bash
npm --version
```

**期望输出**：输出版本号（如 `10.x.x`）。

npm 通常随 Node.js 一同安装。如果 npm 缺失，请重新安装 Node.js。

### 3. 检查 Anthropic API Key

```bash
echo $ANTHROPIC_API_KEY
```

**期望输出**：以 `sk-ant-` 开头的 API Key 字符串。

如果输出为空，说明 API Key 未设置。请按以下方式设置：

```bash
# 临时设置（当前终端会话）
export ANTHROPIC_API_KEY="your-api-key-here"

# 写入 shell 配置文件（推荐，持久生效）
echo 'export ANTHROPIC_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

> **注意**：请将 `your-api-key-here` 替换为你的真实 API Key。切勿将真实 Key 写入日志或版本控制。

## 详细参考

- [Claude Code 安装指引](../../agents/claude-code/README.md) — 完整的安装细节和常见问题
- [隐私保护规则](../../RULES.md) — API Key 的处理必须遵守隐私保护规则

## 确认事项

AI 应在完成检查后向用户报告检查结果，并生成下一步安装计划等待用户确认。
