# Runtime — 软件注册表

本目录是**软件注册表**：登记前置平台、程序语言、工具三类软件的安装目标与关键经验。`workflows/install/selective.md` 对照本清单**按需筛选**要安装的软件。

## 软件注册表

| 软件 | 分类 | 依赖 | 适用场景 | 文档 |
|------|------|------|----------|------|
| [WSL2](./platform/wsl2/README.md) | platform | Windows 10 2004+ / 11 | Windows 用户运行 Linux 开发环境 | `runtime/platform/wsl2/` |
| [Ubuntu](./platform/ubuntu/README.md) | platform | WSL2 或原生 | Linux 系统依赖与基础工具 | `runtime/platform/ubuntu/` |
| [Node.js](./languages/node-js/README.md) | languages | — | Agent 依赖（Claude Code、Codex CLI、OpenCode、Pi） | `runtime/languages/node-js/` |
| [Python](./languages/python/README.md) | languages | — | Agent 依赖（Aider）、数据科学 | `runtime/languages/python/` |
| [Go](./languages/golang/README.md) | languages | — | 后端服务、CLI 工具 | `runtime/languages/golang/` |
| [Shell](./tools/shell/README.md) | tools | — | 终端环境（zsh、PATH、代理） | `runtime/tools/shell/` |

## 筛选规则

1. **platform**：先确认操作系统形态（原生 Linux / WSL2 / 其他），决定是否需要 WSL2
2. **languages**：按要安装的 Agent 的依赖反向筛选（如装 Claude Code → Node.js）
3. **tools**：按日常开发习惯选择（Shell 为可选项）
4. 依赖关系：`platform → languages → agents`（agents 的依赖见 `agents/README.md` 一览表）

## 定位说明

- 本目录属于**知识层**：只描述安装目标与关键经验，不决定执行顺序
- 详细安装步骤以各软件**来源链接**（官方文档）为准，LLM 拉取后自行判断执行
