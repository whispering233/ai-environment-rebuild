# OpenCode

## 概述

开源终端 AI 编码 Agent（支持终端、桌面、IDE 扩展），内置 build / plan 两种 agent，支持 Skills、MCP Servers、LSP 配置。

## 安装目标

- **版本**：最新稳定版
- **方式**：见官方文档（macOS 可用 `brew install opencode`，另有安装脚本、包管理器等方式）
- **前提**：Node.js、LLM API Key

## 来源链接

- 官网：<https://opencode.ai>
- GitHub：<https://github.com/anomalyco/opencode>
- 文档：<https://opencode.ai/docs>

## 配置

- 配置文件：`~/.opencode/opencode.json`（或 `.jsonc`）
- 规则文件：`~/.opencode/AGENTS.md`
- Skills 目录：`~/.opencode/skills/`
- 关键配置项：`agents`（agent 类型）、`skills`（加载 Skill）、`mcpServers`（MCP 扩展）、`lsp`（语言服务器）

## 验证

```bash
opencode --version
```

## 更新

```bash
brew upgrade opencode   # 或对应安装方式的更新命令
```

## 关键注意点

- **不要在 opencode.json 中写入 API Key / Token**；敏感配置放 `~/.opencode/local/`（该目录被 `.gitignore` 排除）或使用环境变量
- MCP 是较新的标准，优先选择支持 MCP 协议的插件；部分插件需要额外依赖（如 Playwright 需要浏览器）
- 内置 Skills（test-driven-development、git-master 等）是 OpenCode 专属机制，其他 Agent 不适用
