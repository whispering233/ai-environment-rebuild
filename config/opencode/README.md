# OpenCode 配置指引

## 概述

OpenCode 是 AI 编码 Agent 的配置文件所在。配置文件为 JSON 格式，控制 Agent 的行为、插件和集成。

## 配置文件位置

- 主配置文件：`~/.opencode/opencode.json` 或 `~/.opencode/opencode.jsonc`
- 规则文件：`~/.opencode/AGENTS.md`
- Skills 目录：`~/.opencode/skills/`

## 关键配置项

### agents

配置可用的 Agent 类型：

```json
{
  "agents": {
    "explore": { "model": "gpt-4o" },
    "build": { "model": "gpt-4o" }
  }
}
```

### skills

Skills 是 AI Agent 的可复用指令集，可加载特定技能的规则：

```json
{
  "skills": {
    "my-skill": {
      "path": "~/.opencode/skills/my-skill/SKILL.md"
    }
  }
}
```

### MCP Servers

MCP（Model Context Protocol）服务器扩展 AI Agent 的能力：

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp"]
    }
  }
}
```

### LSP 配置

语言服务器协议（LSP）配置：

```json
{
  "lsp": {
    "basedpyright": {
      "settings": { "typeCheckingMode": "strict" }
    }
  }
}
```

## 隐私保护

- **不要**在 opencode.json 中写入 API Key 或 Token
- 敏感配置应放在 `~/.opencode/local/` 目录中（该目录被 `.gitignore` 排除）
- 使用环境变量传递密钥更为安全

## AGENTS.md 规则

`~/.opencode/AGENTS.md` 是 AI Agent 的行为规则文件。以下规则应被包含：

- 环境约束（如 WSL2 + Ubuntu）
- 文档习惯（如中文撰写）
- 编码规范（如函数的单一职责原则）
- 安全与隐私规则

## 相关参考

- [OpenCode 官方文档](https://github.com/openai/codex)
- 本项目的 [RULES.md](../../RULES.md) 中的隐私保护规则
- [Shell 配置](../shell/README.md) — 环境变量的设置方法
