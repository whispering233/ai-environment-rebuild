# Full AI Workstation — 完整 AI 工作站搭建

## 适用场景

全新 WSL2 机器，从零搭建完整 AI 工作站。涵盖操作系统配置、语言运行时、AI 编码 Agent、系统配置全链路。

## 前提条件

| 条件 | 说明 |
|------|------|
| 操作系统 | Windows 11（已启用 WSL2） |
| WSL2 | 已安装并配置 |
| 网络 | 能够访问 GitHub、PyPI、npm 等仓库 |
| 磁盘 | 至少 10GB 可用空间 |

## 步骤总览

| 步骤 | 内容 | 引用知识文件 |
|------|------|-------------|
| [Step 1: WSL2 配置](./step-01-prepare-wsl2.md) | WSL2 环境准备和配置 | `platform/wsl2/README.md` |
| [Step 2: 系统基础包](./step-02-system-deps.md) | Ubuntu 基础包安装 | `platform/ubuntu/README.md` |
| [Step 3: 安装 Node.js](./step-03-install-nodejs.md) | Node.js 运行时安装 | `runtime/node-js/README.md` |
| [Step 4: 安装 Python](./step-04-install-python.md) | Python 运行时安装 | `runtime/python/README.md` |
| [Step 5: 安装 Go](./step-05-install-golang.md) | Go 语言运行时安装 | `runtime/golang/README.md` |
| [Step 6: 安装 AI Agents](./step-06-install-agents.md) | Claude Code、Codex CLI 等 Agent 安装 | `agents/claude-code/README.md`, `agents/codex-cli/README.md` |
| [Step 7: 配置并验证](./step-07-configure-verify.md) | 全局配置 + 全链路验证 | `config/shell/README.md`, `config/opencode/README.md` |

## 使用流程

1. AI 依次阅读各步骤文件
2. 生成定制安装计划（包含具体命令）
3. 提交计划等待用户批准
4. 按批准后的计划执行

## 相关链接

- [工作流路由表](../README.md)
- [WSL2 平台依赖](../../platform/wsl2/README.md)
- [Ubuntu 环境依赖](../../platform/ubuntu/README.md)
- [Node.js 安装指引](../../runtime/node-js/README.md)
- [Python 安装指引](../../runtime/python/README.md)
- [Go 安装指引](../../runtime/golang/README.md)
- [Claude Code 安装指引](../../agents/claude-code/README.md)
- [Codex CLI 安装指引](../../agents/codex-cli/README.md)
- [全局规则](../../RULES.md)
