# AI Environment Rebuild

> 当前版本：**v0.1.1**（2026-08-18）

一个给 AI 阅读和执行的环境搭建编排项目。**本项目只编排安装顺序和安装目标，不是详细严格的安装步骤说明** —— 详细步骤由 LLM 拉取各条目的来源链接自行判断执行。

> **使用方式**：用户给 LLM 本项目的 GitHub 链接，LLM 读取后生成会话内计划并执行。

## 项目结构

```
.
├── commons/          # 通用层：AGENTS.md（全局规则，源为 gist）、skills/plugins 通用清单
├── agents/           # AI Agent 安装知识（按工具自包含）
├── runtime/          # 软件注册表：前置平台、程序语言、工具（按需筛选的依据）
├── workflows/        # 编排层：安装（全量/按需）+ 更新工作流
├── doc/design/       # 设计文档：架构设计、任务卡片清单
├── README.md         # 本项目文件（AI 路由入口）
├── CHANGELOG.md
├── LICENSE
└── .env.example      # 配置模板
```

## AI 路由规则

1. **理解项目**：阅读本文件了解结构与定位
2. **拉取全局规则**：按 [commons/AGENTS.md](./commons/AGENTS.md) 从 gist 拉取全局规则，作为本次会话的约束
3. **选择工作流**：前往 [workflows/README.md](./workflows/README.md) 按场景选择（全量安装 / 按需安装 / 更新）
4. **生成计划**：按工作流步骤生成计划（软件清单、依赖、风险），提交用户审批
5. **执行**：获得批准后按计划执行，引用 `agents/`、`runtime/` 对应知识文档；详细命令以文档中的来源链接为准

## 相关文件

- [workflows/README.md](./workflows/README.md) — 工作流路由
- [commons/AGENTS.md](./commons/AGENTS.md) — 全局规则说明（源：gist）
- [.env.example](./.env.example) — 配置模板
