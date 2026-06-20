# 推荐 Skills 列表

以下是开发和维护 AI 环境时推荐的 Skills。

## Skill 列表

| Skill 名称 | 来源 | 用途 |
|------------|------|------|
| **test-driven-development** | OpenCode 内置 | 先写测试再写实现的开发流程，确保代码质量 |
| **git-master** | OpenCode 内置 | Git 操作最佳实践，包括原子提交、rebase、squash 等 |
| **debugging** | OpenCode 内置 | 系统性调试流程，假设驱动、根因分析、修复验证 |
| **writing-plans** | OpenCode 内置 | 多步骤任务前编写实施计划，确保方案经过审阅 |
| **brainstorming** | OpenCode 内置 | 创意工作前的需求分析和方案设计探索 |
| **review-work** | OpenCode 内置 | 实施后审查，多角度并行验证交付质量 |
| **karpathy-guidelines** | OpenCode 内置 | 减少常见 AI 编码错误的指导原则 |
| **systematic-debugging** | OpenCode 内置 | 遇到 Bug 时的系统性排查与修复流程 |
| **verification-before-completion** | OpenCode 内置 | 任务完成前的验证检查，确保无遗漏 |
| **executing-plans** | OpenCode 内置 | 按编写好的计划分批执行，含审查检查点 |

## 按场景推荐

### 新功能开发

推荐按以下顺序加载 Skills：

1. **brainstorming** — 需求分析与设计方案
2. **writing-plans** — 编写实施计划
3. **test-driven-development** — 测试驱动开发
4. **verification-before-completion** — 完成前验证

### 日常开发维护

1. **git-master** — 版本控制操作
2. **debugging** / **systematic-debugging** — Bug 修复
3. **review-work** — 代码审查

### 优化与重构

1. **karpathy-guidelines** — 避免过度设计
2. **executing-plans** — 分批执行复杂任务
3. **review-work** — 审查变更质量

## 如何创建自定义 Skill

可参照 [writing-skills Skill](https://github.com/openai/codex) 的文档创建自定义 Skill。

基本步骤：

1. 在 `~/.opencode/skills/` 下创建子目录，如 `my-skill/`
2. 创建 `SKILL.md` 文件，包含 Skill 的名称、触发条件和执行步骤
3. 在 opencode.json 中注册该 Skill
4. 验证 Skill 可正常加载和使用
