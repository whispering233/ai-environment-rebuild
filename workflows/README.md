# Workflows — 工作流路由

工作流是**编排层**：决定安装/更新的顺序与筛选逻辑。知识（目标、链接、经验）在 `agents/`、`runtime/`、`commons/`，本目录不重复细节，只编排。

## 工作流路由表

| 工作流 | 适用场景 | 入口 |
|--------|----------|------|
| [install/full-workstation](./install/full-workstation.md) | 全新机器，从零搭建完整 AI 工作站 | `workflows/install/full-workstation.md` |
| [install/selective](./install/selective.md) | 已有部分环境，按需筛选安装 | `workflows/install/selective.md` |
| [update/update](./update/update.md) | 更新 agents / runtime / commons | `workflows/update/update.md` |

## 通用执行纪律

1. **先拉取全局规则**：执行任何工作流前，先按 [commons/AGENTS.md](../commons/AGENTS.md) 的说明从 gist 拉取全局规则，作为本次会话的约束
2. **计划审批**：生成安装/更新计划（内容、预期变更、风险）后，必须获得用户明确批准才能执行修改操作
3. **隐私保护**：API Key 等敏感信息使用占位符，绝不写入日志、文件或版本控制
4. **知识引用**：每步执行时引用对应知识文档（`agents/<tool>/README.md`、`runtime/<...>/README.md`）；详细命令以知识文档中的来源链接为准，LLM 拉取后自行判断执行
