# Pi

## 概述

极简终端编码 harness（AI coding assistant）。以 TypeScript 扩展（Extensions）、Skills、Prompt Templates、Themes、Pi Packages 方式适配个人工作流，无需 fork 修改内部。支持交互式 / print / JSON / RPC / SDK 多种模式。

## 安装目标

- **版本**：最新稳定版（npm）
- **方式**：
  ```bash
  npm install -g --ignore-scripts @earendil-works/pi-coding-agent
  ```
  或官方安装脚本：`curl -fsSL https://pi.dev/install.sh | sh`
- **前提**：Node.js、LLM API Key（如 `ANTHROPIC_API_KEY`）

## 来源链接

- 官网：<https://pi.dev>
- npm 包：<https://www.npmjs.com/package/@earendil-works/pi-coding-agent>
- 文档（本地安装后）：`docs/` 目录（README.md、extensions.md、skills.md、themes.md、prompt-templates.md、sdk.md 等）

## 配置

- API Key：环境变量（`pi auth` 可检查 provider 就绪状态）
- 扩展管理：`pi install <source>` / `pi remove <source>` / `pi list`（settings 控制）
- 资源开关：`pi config`（TUI 启停 skills、prompt templates 等包资源）

## 验证

```bash
pi --version
```

## 更新

```bash
pi update        # 更新 pi 自身、扩展、模型目录
```

## 关键注意点

- 安装必须带 `--ignore-scripts`（pi 不需要依赖生命周期脚本）
- 扩展 / Skills / Themes 等可打包为 Pi Packages 通过 npm 或 git 分享
- 项目级指令文件（AGENTS.md）会被 pi 自动读取为项目上下文
