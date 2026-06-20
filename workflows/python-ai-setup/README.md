# Python AI Setup — Python + AI 从零搭建

## 适用场景

从零搭建 Python AI 开发环境，包括 Python 运行时、AI 编码 Agent、Shell 环境配置。

## 前提条件

| 条件 | 说明 |
|------|------|
| 操作系统 | Ubuntu / WSL2 Ubuntu |
| 包管理器 | apt（通常预装） |
| 网络 | 能够访问 GitHub、PyPI、npm 仓库 |

## 步骤总览

| 步骤 | 内容 | 引用知识文件 |
|------|------|-------------|
| [Step 1: 检测平台](./step-01-detect-platform.md) | 检测操作系统、包管理器、系统状态 | `platform/ubuntu/README.md` |
| [Step 2: 安装 Python](./step-02-install-python.md) | 安装 Python + pip + pyenv | `runtime/python/README.md` |
| [Step 3: 安装 AI Agent](./step-03-install-agent.md) | 安装 AI Agent（Claude Code / Codex CLI） | `agents/claude-code/README.md`, `agents/codex-cli/README.md` |
| [Step 4: 配置环境](./step-04-configure.md) | 配置 API Key、Shell 环境 | `config/shell/README.md`, `config/opencode/README.md` |
| [Step 5: 验证完整链路](./step-05-verify.md) | 验证 Python + Agent 全链路可用 | `runtime/python/README.md`, `agents/claude-code/README.md` |

## 使用流程

1. AI 依次阅读各步骤文件
2. 生成定制安装计划（包含具体命令）
3. 提交计划等待用户批准
4. 按批准后的计划执行

## 相关链接

- [工作流路由表](../README.md)
- [Ubuntu 环境依赖](../../platform/ubuntu/README.md)
- [Python 安装指引](../../runtime/python/README.md)
- [Claude Code 安装指引](../../agents/claude-code/README.md)
- [Codex CLI 安装指引](../../agents/codex-cli/README.md)
- [全局规则](../../RULES.md)
