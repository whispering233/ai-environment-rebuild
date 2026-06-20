# Workflows — 工作流路由表

工作流是**编排层**，决定先安装什么后安装什么。每个工作流引用知识层文件中的详细安装要点。

## 如何选择工作流

AI 的工作流程：

1. **了解用户需求** — 询问用户当前环境状态和安装目标
2. **匹配工作流** — 根据用户场景从下方路由表中选择最合适的工作流
3. **生成计划** — 按工作流步骤生成定制安装计划
4. **用户确认** — 提交计划等待用户批准
5. **执行** — 按批准后的计划逐步执行，引用知识层文件中的详细内容

## 工作流路由表

| 工作流 | 适用场景 | 需要前提 | 包含内容 |
|--------|----------|----------|----------|
| [claude-code-quick](./claude-code-quick/README.md) | 已有开发环境，只需安装 Claude Code | Node.js 18+, Anthropic API Key | Claude Code 安装+验证 |
| [python-ai-setup](./python-ai-setup/README.md) | Python + AI 编码工具从零搭建 | Ubuntu/WSL2 | Python + Agent + 配置 |
| [full-ai-workstation](./full-ai-workstation/README.md) | 全新 WSL2 机器，完整工作站 | WSL2 已启用 | 全部 |

## 重要说明

> **工作流不包含安装脚本**。工作流仅描述执行步骤和顺序，每步由 AI 在对话中生成定制计划并与用户确认后执行。具体的安装命令、配置参数、注意事项等详细内容，请在对应步骤中引用知识层子目录（`agents/`、`platform/`、`runtime/`、`config/`等）的相关文件获取。

## 知识层 vs 编排层

本目录属于**编排层**，与知识层分离：

- **编排层**（`workflows/`）：决定执行顺序和步骤
- **知识层**（`agents/`、`platform/`、`runtime/`、`config/`、`skills/`、`plugins/`、`notes/`）：提供详细的安装知识和操作指引

AI 不得直接按知识层文件的目录顺序执行；必须通过工作流确定执行顺序。详细规则请参阅 [RULES.md](../RULES.md)。

## 相关文件

- [INDEX.md](../INDEX.md) — 项目入口和整体结构
- [RULES.md](../RULES.md) — AI 执行规则（含知识/编排分离、计划审批等约束）
