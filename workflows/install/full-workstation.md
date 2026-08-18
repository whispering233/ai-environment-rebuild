# 全量安装 — Full Workstation

## 适用场景

全新 WSL2 机器，从零搭建完整 AI 工作站（平台 + 语言 + 工具 + 全部 Agents）。

## 前提条件

| 条件 | 说明 |
|------|------|
| 操作系统 | Windows 11（已启用 WSL2）或原生 Linux |
| 网络 | 能访问 GitHub、PyPI、npm 等仓库 |
| 磁盘 | 至少 10GB 可用空间 |

## 步骤编排

| 步骤 | 内容 | 引用知识文档 |
|------|------|-------------|
| 0 | 拉取全局规则（gist） | `commons/AGENTS.md` |
| 1 | 平台：WSL2 配置 + Ubuntu 基础包 | `runtime/platform/wsl2/README.md`、`runtime/platform/ubuntu/README.md` |
| 2 | 语言：Node.js + Python + Go | `runtime/languages/node-js/README.md`、`runtime/languages/python/README.md`、`runtime/languages/golang/README.md` |
| 3 | 工具：Shell 环境 | `runtime/tools/shell/README.md` |
| 4 | Agents：Claude Code + Codex CLI + Aider + OpenCode + Pi（与用户确认安装哪些） | `agents/*/README.md` |
| 5 | 配置与验证：API Key（占位符）、PATH、全链路验证 | 各知识文档的"配置/验证"章节 |

## 执行要求

- 每步执行前生成计划并与用户确认（含安装内容、预期变更、风险）
- 详细命令以知识文档的来源链接为准，LLM 拉取官方文档后自行判断执行
- 安装完成后按各文档"验证"章节逐项确认
