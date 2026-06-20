# Plugins — 推荐 Plugins

Plugins 是 AI Agent 功能的扩展，通过 MCP（Model Context Protocol）或 Agent 内置的插件系统增强 Agent 的能力，使其能够访问外部工具和数据源。

## Plugin 类型

- **MCP Servers**：通过 Model Context Protocol 与 AI Agent 通信的服务端插件
- **Agent 内置扩展**：Agent 自身支持的插件机制（如 Claude Code 的 tools）
- **自定义插件**：根据需求自行开发的插件

## 注意事项

- Plugin 的兼容性取决于 AI Agent 的版本和支持协议
- MCP 是较新的标准，优先选择支持 MCP 协议的插件
- 部分插件需要额外的依赖（如 Playwright 需要浏览器）
- 安全考虑：运行第三方插件时注意代码审计

## 推荐 Plugin 列表

查看 [plugins/lists/recommended.md](./lists/recommended.md) 获取推荐的 Plugin 清单。

## 知识层说明

本目录属于**知识层**，只列出推荐的 Plugins，不涉及具体的安装顺序。安装顺序由 [workflows/](../workflows/README.md) 中的工作流决定。

关于项目整体结构、知识层与编排层的分离规则，请参阅 [INDEX.md](../INDEX.md) 和 [RULES.md](../RULES.md)。
