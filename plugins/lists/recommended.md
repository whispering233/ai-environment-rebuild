# 推荐 Plugins 列表

以下是开发和维护 AI 环境时推荐的 Plugins。

## Plugin 列表

| Plugin 名称 | 来源 | 用途 |
|-------------|------|------|
| **Playwright MCP** | Microsoft | 浏览器自动化，支持 Web 页面交互、截图、信息抓取和 E2E 测试 |
| **GitHub MCP** | GitHub | GitHub API 集成，管理 Issue、PR、代码审查和工作流 |
| **Filesystem MCP** | Anthropic | 安全的文件系统访问，提供受限的文件读写和目录操作能力 |
| **Docker MCP** | 社区 | Docker 容器管理，支持镜像构建、容器启动和日志查看 |
| **SQLite MCP** | 社区 | SQLite 数据库查询和操作，适用于本地数据存储和调试 |
| **Memory MCP** | 社区 | AI Agent 持久化记忆管理，跨会话保持上下文信息 |
| **Puppeteer MCP** | 社区 | 基于 Puppeteer 的浏览器自动化，另一种 Web 交互选择 |
| **Fetch MCP** | Anthropic | HTTP 请求工具，支持 Web 内容获取和 API 调用 |

## 按场景推荐

### Web 自动化

| Plugin | 优先级 | 替代选择 |
|--------|--------|----------|
| Playwright MCP | 首选 | Puppeteer MCP |
| Fetch MCP | 辅助 | — |

### 版本控制与协作

| Plugin | 优先级 | 说明 |
|--------|--------|------|
| GitHub MCP | 推荐 | 管理 Issue/PR/Code Review |
| Filesystem MCP | 必需 | 文件操作的基础插件 |

### 数据库操作

| Plugin | 优先级 | 说明 |
|--------|--------|------|
| SQLite MCP | 本地开发 | 轻型数据库操作 |
| （其他数据库 MCP） | 按需选择 | PostgreSQL、MySQL 等 |

## 安装 MCP Server

MCP Server 通常通过 opencode.json 配置：

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp"]
    },
    "github": {
      "command": "node",
      "args": ["path/to/github-mcp-server"]
    }
  }
}
```

## 安全提示

- 仅安装来自可信来源的 Plugin
- 定期更新 Plugin 版本以获取安全修复
- 避免在 Plugin 配置中硬编码敏感凭据
- 了解 Plugin 所需的权限范围，遵循最小权限原则
