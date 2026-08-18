# 任务卡片清单

## 里程碑

| 里程碑 | 版本 | 状态 |
|--------|------|------|
| M1 初始骨架 | v0.1.0 | ✅ 完成 |
| M2 结构简化（commons/agents/runtime/workflows） | v0.1.1 | ✅ 完成 |

## v0.1.1 任务卡片（M2 结构简化）

- [x] T1 新建 `commons/`：AGENTS.md（gist 为源，安装/更新时拉取覆盖）、通用 skills/plugins 清单（名称+来源链接）
- [x] T2 重构 `agents/`：知识自包含；新增 opencode、pi；全部精简为「概述/安装目标/来源链接/配置/验证/更新/关键注意点」
- [x] T3 重构 `runtime/`：软件注册表（platform/languages/tools 三分类 + 筛选规则），供按需筛选
- [x] T4 收敛 `workflows/`：install/full-workstation + install/selective + update/update（含 commons gist 覆盖更新）
- [x] T5 根文件：README.md 重写（吸收 INDEX.md 路由职责）；删除 platform/config/skills/plugins/notes、RULES.md、INDEX.md、旧工作流
- [x] T6 收尾：CHANGELOG.md 落版 v0.1.1、架构设计文档、文档互链验证、发布
