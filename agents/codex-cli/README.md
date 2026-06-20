# Codex CLI 安装指引

## 概述

Codex CLI 是 OpenAI 推出的 AI 编码 Agent，基于 OpenAI Codex / GPT 系列模型，提供终端内 AI 辅助编码能力。与 Claude Code 类似，但底层基于 OpenAI 模型生态。

## 前提条件

| 条件 | 说明 |
|------|------|
| Node.js | 版本 18+（建议 20 LTS） |
| npm | 随 Node.js 一同安装 |
| API Key | 有效的 OpenAI API Key（从 [platform.openai.com](https://platform.openai.com/api-keys) 获取） |
| 终端 | Bash / Zsh（WSL2 Ubuntu 环境下建议使用 Bash） |

## 安装方法

### 全局安装（推荐）

```bash
npm install -g @openai/codex
```

全局安装后可在任意目录直接执行 `codex` 命令。

## 分步安装指南

### 步骤 1：确认 Node.js 版本

```bash
node --version
# 应输出 v18.x.x 或更高版本
```

如果版本低于 18，请先升级 Node.js（参见 [runtime/](../../runtime/README.md) 中的 Node.js 安装指引）。

### 步骤 2：安装 Codex CLI

```bash
npm install -g @openai/codex
```

### 步骤 3：配置 API Key

设置环境变量 `OPENAI_API_KEY`：

```bash
# 临时设置（当前终端会话）
export OPENAI_API_KEY="your-api-key-here"

# 写入 shell 配置文件（推荐，持久生效）
echo 'export OPENAI_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

> **注意**：请将 `your-api-key-here` 替换为你的真实 API Key。切勿将真实 Key 提交到版本控制。

## 配置位置

- 配置文件目录：`~/.codex/`
- 包含认证凭据、模型偏好等配置

## 验证安装

```bash
codex --version
```

如输出版本号，说明安装成功。你也可以直接运行 `codex` 进入交互模式测试。

## WSL2 注意事项

- WSL2 环境下确保 Node.js 是 Linux 版本（而非 Windows 版本）
- 如果终端路径中包含 Windows 的 npm 路径，可能会导致冲突。建议在 WSL2 中使用 `nvm` 管理 Node.js 版本
- 环境变量建议在 `~/.bashrc` 中配置（而非 Windows 的环境变量），确保在 WSL2 会话中生效

## 常见问题

### 1. 权限错误（EACCES）

全局安装时遇到权限错误，可使用 `nvm` 管理 Node.js 以避免 sudo 需求，或修复 npm 权限：

```bash
# 使用 nvm 安装 Node.js（推荐）
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash
nvm install 20
```

### 2. `codex` 命令找不到

检查 npm 全局 bin 目录是否在 PATH 中：

```bash
npm bin -g
export PATH="$(npm bin -g):$PATH"
```

### 3. API Key 未生效

确认 `OPENAI_API_KEY` 已正确设置且在当前终端会话中可用：

```bash
echo $OPENAI_API_KEY
```

输出不应为空。如为空，请重新加载 shell 配置文件（`source ~/.bashrc`）。

## 相关规则

- **隐私保护**：API Key 的处理请严格遵守 [RULES.md](../../RULES.md) 中的隐私保护规则，禁止泄露到日志或版本控制。
- **计划审批**：安装前应生成计划并等待用户批准，遵循 [RULES.md](../../RULES.md) 的计划审批规则。
