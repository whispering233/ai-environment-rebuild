# Skills — 推荐 Skills

Skills 是 AI Agent 的可复用指令集，定义了特定任务的执行方式。加载 Skill 后，AI Agent 会按照 Skill 中定义的步骤、规则和约束来完成任务。

## Skills 来源

- **OpenCode 内置 Skills**：跟随 OpenCode CLI 安装，位于 `~/.opencode/skills/` 或 `~/.config/opencode/skills/`
- **自定义 Skills**：用户自行编写的 Skill 规则，可放在 `~/.opencode/skills/` 下
- **社区共享 Skills**：由社区维护的 Skills 集合

## 如何加载 Skills

在 AI Agent 配置中声明要加载的 Skills：

```json
{
  "load_skills": ["test-driven-development", "git-master", "debugging"]
}
```

或在任务描述中指明：

```
请按照 test-driven-development Skill 的流程执行本任务。
```

## 推荐 Skill 列表

查看 [skills/lists/recommended.md](./lists/recommended.md) 获取推荐的 Skill 清单。

## 知识层说明

本目录属于**知识层**，只列出推荐的 Skills，不涉及具体的执行计划。执行顺序由 [workflows/](../workflows/README.md) 中的工作流决定。

关于项目整体结构、知识层与编排层的分离规则，请参阅 [INDEX.md](../INDEX.md) 和 [RULES.md](../RULES.md)。
