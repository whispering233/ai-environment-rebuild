# Aider

## 概述

开源 AI 结对编程工具，支持多种 LLM 后端（OpenAI、Anthropic 等），自动管理 git 提交并协调 AI 与用户的编辑。

## 安装目标

- **版本**：最新稳定版
- **方式**：`pip install aider-chat`（或 `uv tool install aider-chat`、`pipx install aider-chat` 隔离安装）
- **前提**：Python 3.10+、Git 2.x+、任意兼容的 LLM API Key

## 来源链接

- 官方文档：<https://aider.chat/docs/>
- 安装文档：<https://aider.chat/docs/install.html>

## 配置

- API Key：项目目录 `.env` 文件（加入 `.gitignore`）或环境变量 `ANTHROPIC_API_KEY` / `OPENAI_API_KEY`
- 多模型：`aider --model <model>` 指定，`aider --models` 查看可用模型

## 验证

```bash
aider --version
```

## 更新

```bash
pip install -U aider-chat
```

## 关键注意点

- 安装后 `aider` 命令找不到：`export PATH="$HOME/.local/bin:$PATH"`（pip --user 安装路径）
- Aider 需在 Git 仓库中工作，非仓库目录首次运行会提示 `git init`
- 推荐使用 `uv tool install` 或 pipx 隔离安装，避免系统 Python 环境被污染
