# Changelog

本文件记录项目的所有显著变动。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，
版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [v0.1.1] - 2026-08-18

### Changed
- 结构简化：由 8 目录收敛为 `commons/`、`agents/`、`runtime/`、`workflows/` 四类
  - `commons/`：新增，含 AGENTS.md（全局规则，源为 gist，安装/更新时拉取）、通用 skills/plugins 清单（名称+来源链接）
  - `agents/`：新增 opencode、pi 安装说明；全部 agent 文档精简为方案 B 格式（概述/安装目标/来源链接/配置/验证/更新/关键注意点）
  - `runtime/`：软件注册表（platform/languages/tools），供按需筛选；原 `platform/`、`config/shell` 并入
  - `workflows/`：收敛为 2 个安装工作流（全量/按需）+ 1 个更新工作流（含 commons gist 覆盖更新）
- 文档定位：只编排安装顺序和安装目标，详细步骤以各条目来源链接（官方文档）为准

### Removed
- 删除 `platform/`、`config/`、`skills/`、`plugins/`、`notes/` 目录及 `RULES.md`、`INDEX.md`
- 删除旧工作流 claude-code-quick、python-ai-setup、full-ai-workstation 及其 step 文件


## [v0.1.0] - 2026-06-20

### Added
- 初始版本：初始化github发布工作流，添加README.md
- 项目骨架，初始化项目骨架