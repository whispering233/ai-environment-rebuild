# 系统架构设计

## 项目定位

AI 环境搭建**编排项目**：只编排安装顺序和安装目标，不是详细严格的安装步骤说明。详细步骤由 LLM 拉取各条目的来源链接（官方文档）自行判断执行。

## 使用模式

```
用户给 LLM 本项目 GitHub 链接
  → LLM 阅读 README.md（路由入口）
  → 按 commons/AGENTS.md 从 gist 拉取全局规则（本次会话约束）
  → 按 workflows/README.md 选择工作流
  → 生成计划 → 用户审批 → 执行（引用 agents/、runtime/ 知识文档）
```

## 四层结构

| 层 | 目录 | 职责 |
|----|------|------|
| 通用层 | `commons/` | 全局规则（AGENTS.md，单一内容源 gist，无版本号覆盖式更新）、通用 skills/plugins 清单（名称+来源链接） |
| 知识层 | `agents/` | Agent 知识自包含：安装目标、来源链接、配置/验证/更新要点、关键经验 |
| 知识层 | `runtime/` | 软件注册表：platform（前置平台）/ languages（程序语言）/ tools（工具），登记依赖与适用场景 |
| 编排层 | `workflows/` | 安装（全量 / 按需筛选）+ 更新（agents/runtime/commons）流程编排 |

## 核心机制

### 1. 知识 / 编排分离

- 知识层（commons/agents/runtime）只描述"装什么、注意什么"，不决定顺序
- 编排层（workflows）决定"先装什么后装什么"，只引用知识文档不重复细节

### 2. 软件注册表 + 按需筛选

- `runtime/README.md` 是注册表总清单（软件/分类/依赖/适用场景/文档）
- `workflows/install/selective.md` 按依赖链反向筛选：agent 依赖 → languages → platform → tools

### 3. 单一内容源

- `commons/AGENTS.md`：内容源为 gist，无版本号，安装/更新时**一律拉取覆盖**
- 知识文档的安装细节：以各条目**来源链接**（官方文档）为唯一准绳，本地不复制教程，避免漂移

## 设计原则

- **YAGNI**：不做详细教程维护、不预拆多文件（单文件章节化，内容膨胀后再拆）
- **自包含**：agent 知识不跨目录引用，专属 skill/plugin 随 agent 文档
- **筛选显式化**：注册表清单使"筛选"成为 workflow 的显式流程步骤
