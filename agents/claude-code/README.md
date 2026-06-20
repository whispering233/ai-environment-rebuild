# Claude Code 安装指引

## 概述

Claude Code 是 Anthropic 推出的 AI 编码 Agent，基于 Claude 模型，提供终端内 AI 辅助编码能力，支持代码生成、重构、调试、文件操作等工作流。

## 前提条件

| 条件 | 说明 |
|------|------|
| Node.js | 版本 18+（建议 20 LTS） |
| npm | 随 Node.js 一同安装 |
| API Key | 有效的 Anthropic API Key（从 [console.anthropic.com](https://console.anthropic.com) 获取） |
| 终端 | Bash / Zsh（WSL2 Ubuntu 环境下建议使用 Bash） |

## 安装方法

### 方法一：npx（推荐，无需全局安装）

```bash
npx @anthropic-ai/claude-code init
```

### 方法二：npm 全局安装

```bash
npm install -g @anthropic-ai/claude-code
```

全局安装后可在任意目录直接执行 `claude` 命令。

### 方法三：直接运行（临时使用）

```bash
npx @anthropic-ai/claude-code
```

## 分步安装指南

### 步骤 1：确认 Node.js 版本

```bash
node --version
# 应输出 v18.x.x 或更高版本
```

如果版本低于 18，请先升级 Node.js（参见 [runtime/](../../runtime/README.md) 中的 Node.js 安装指引）。

### 步骤 2：安装 Claude Code

选择上述任一安装方法。推荐使用 `npx` 方式：

```bash
npx @anthropic-ai/claude-code init
```

### 步骤 3：配置 API Key

设置环境变量 `ANTHROPIC_API_KEY`：

```bash
# 临时设置（当前终端会话）
export ANTHROPIC_API_KEY="your-api-key-here"

# 写入 shell 配置文件（推荐，持久生效）
echo 'export ANTHROPIC_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

> **注意**：请将 `your-api-key-here` 替换为你的真实 API Key。切勿将真实 Key 提交到版本控制。

## 配置位置

- 配置文件目录：`~/.claude/`
- 包含认证凭据、模型偏好等配置

## 验证安装

```bash
claude --version
```

如输出版本号，说明安装成功。你也可以直接运行 `claude` 进入交互模式测试。

## 常见问题

### 1. `npx` 安装速度慢

可尝试设置 npm 镜像源加速：

```bash
npm config set registry https://registry.npmmirror.com
```

### 2. "command not found: claude"

全局安装后如果找不到命令，可能是因为 npm 全局 bin 目录未在 PATH 中。检查并添加：

```bash
# 查看 npm 全局 bin 路径
npm bin -g

# 将其添加到 PATH（例如 ~/.bashrc）
export PATH="$(npm bin -g):$PATH"
```

### 3. API Key 格式错误

确保 `ANTHROPIC_API_KEY` 的值以 `sk-ant-` 开头，且不含多余空格或换行符。

## 相关规则

- **隐私保护**：API Key 的处理请严格遵守 [RULES.md](../../RULES.md) 中的隐私保护规则，禁止泄露到日志或版本控制。
- **计划审批**：安装前应生成计划并等待用户批准，遵循 [RULES.md](../../RULES.md) 的计划审批规则。
