# Codex CLI

## 概述

OpenAI 推出的终端内 AI 编码 Agent，底层基于 OpenAI Codex / GPT 系列模型。

## 安装目标

- **版本**：最新稳定版
- **方式**：`npm install -g @openai/codex`（另有 Homebrew、官方安装脚本等，见官方文档）
- **前提**：Node.js 18+、有效的 OpenAI API Key（或 ChatGPT 账号登录）

## 来源链接

- GitHub：<https://github.com/openai/codex>
- 官方文档：<https://developers.openai.com/codex>

## 配置

- 配置目录：`~/.codex/`（认证凭据、模型偏好）
- API Key 通过环境变量 `OPENAI_API_KEY` 提供，勿写入配置文件或提交版本控制

## 验证

```bash
codex --version
```

## 更新

```bash
npm update -g @openai/codex
```

## 关键注意点

- **WSL2 环境**：确保使用 Linux 版 Node.js（`which node` 应指向 `~/.nvm/...` 而非 `/mnt/c/...`），环境变量在 `~/.bashrc` 配置
- 全局安装权限错误（EACCES）：使用 nvm 管理 Node.js 可避免 sudo
- 推荐 Skill / Plugin（如 MCP）配置方式见官方文档，按需自行拉取判断
