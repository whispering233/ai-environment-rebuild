# AI Environment Rebuild

AI Environment Rebuild - 一个给AI阅读和执行的工作流项目，帮助AI快速在各种环境中搭建AI工作环境。包括环境依赖、各大 Agent Code、方便的 Agent Utils、配置路径设置、用户规则文件、推荐的 Skills、推荐的 Plugins、注意事项和易错点。

> **AI 路由规则**: AI阅读完毕后，请先阅读 [INDEX.md](./INDEX.md) 了解项目结构和路由规则，再根据 [RULES.md](./RULES.md) 的约束执行工作。

## 项目包含

- **环境依赖** — WSL2、Ubuntu 等平台依赖安装
- **Agent Code** — Claude Code、Codex CLI、Aider 等 AI Agent 安装
- **Agent Utils** — 辅助工具和脚本
- **配置设置** — OpenCode、Shell 等配置文件指引
- **规则文件** — AI 执行时必须遵守的全局规则
- **Skills** — 推荐的 Skills 列表
- **Plugins** — 推荐的 Plugins 列表
- **注意事项** — 安装和使用中的易错点

## 项目结构

```
.
├── agents/        # AI Agent 安装知识
├── platform/      # 平台环境依赖
├── runtime/       # 语言运行时安装
├── config/        # 配置文件指引
├── skills/        # 推荐 Skills 列表
├── plugins/       # 推荐 Plugins 列表
├── notes/         # 注意事项和易错点
├── workflows/     # 可选工作流（按场景选择）
├── INDEX.md       # AI 入口文件
├── RULES.md       # 全局规则
└── .env.example   # 配置模板
```
