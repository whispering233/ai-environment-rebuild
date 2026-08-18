# Claude Code

## 概述

Anthropic 推出的终端内 AI 编码 Agent，支持代码生成、重构、调试、文件操作等工作流。

## 安装目标

- **版本**：最新稳定版
- **方式**：`npm install -g @anthropic-ai/claude-code`（或 `npx @anthropic-ai/claude-code init` 免全局安装）
- **前提**：Node.js 18+（建议 20 LTS）、有效的 Anthropic API Key（以 `sk-ant-` 开头）

## 来源链接

- 官方文档：<https://code.claude.com/docs/en/overview>
- npm 包：<https://www.npmjs.com/package/@anthropic-ai/claude-code>

## 配置

- 配置目录：`~/.claude/`（认证凭据、模型偏好）
- API Key 通过环境变量 `ANTHROPIC_API_KEY` 提供，勿写入配置文件或提交版本控制

## 验证

```bash
claude --version
```

## 更新

```bash
npm update -g @anthropic-ai/claude-code
```

## 关键注意点

- 全局安装后 `command not found: claude`：npm 全局 bin 目录不在 PATH，`export PATH="$(npm bin -g):$PATH"`
- 国内网络 `npx` 安装慢：可配置 npm 镜像源 `npm config set registry https://registry.npmmirror.com`
- 推荐 Skill / Plugin（如 MCP）配置方式见官方文档，按需自行拉取判断
