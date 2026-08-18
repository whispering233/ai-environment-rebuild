# 按需安装 — Selective

## 适用场景

已有部分环境（或全新但需求明确），只需安装指定软件/Agent。覆盖"只装某个 Agent"、"Python + AI"等任意组合场景。

## 核心流程

```
问需求 → 对照注册表筛选 → 生成计划 → 用户审批 → 执行 → 验证
```

### 步骤 1：拉取全局规则

按 [commons/AGENTS.md](../../commons/AGENTS.md) 从 gist 拉取全局规则，作为本次会话约束。

### 步骤 2：询问用户需求

- 当前环境状态：操作系统形态（原生 Linux / WSL2 / macOS）、已有运行时与工具
- 安装目标：要装哪些 Agent、哪些语言/工具
- 使用场景：用途决定筛选（如"只要 Claude Code"、"Python + Aider"）

### 步骤 3：对照注册表筛选

对照 [runtime/README.md](../../runtime/README.md) 软件注册表，按依赖关系反向筛选：

1. 按 Agent 依赖确定 languages（见 [agents/README.md](../../agents/README.md) 一览表）
2. 按操作系统形态确定 platform 是否需要
3. 按用户习惯确定 tools
4. 输出筛选后的软件清单（含依赖链）

### 步骤 4：生成计划

计划包含：软件清单、依赖关系、预期变更、可能风险。提交用户审批。

### 步骤 5：执行

按依赖顺序（platform → languages → tools → agents）逐项执行，每项引用对应知识文档：

- Agents：`agents/<tool>/README.md`
- 平台/语言/工具：`runtime/<分类>/<软件>/README.md`

详细命令以各知识文档的**来源链接**为准，LLM 拉取官方文档后自行判断执行。

### 步骤 6：验证

按各知识文档"验证"章节逐项确认；API Key 用占位符配置，不落盘真实值。

## 可选的 Skills / Plugins

- 通用清单见 [commons/skills.md](../../commons/skills.md)、[commons/plugins.md](../../commons/plugins.md)
- Agent 专属的见对应 `agents/<tool>/README.md`
- LLM 自行拉取清单来源链接判断如何获取与安装
