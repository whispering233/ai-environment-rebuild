# Platform — 平台环境依赖

OS 平台依赖安装知识，包括 WSL2 和 Ubuntu 的环境准备。

## 平台一览

| 平台 | 适用场景 | 主要内容 |
|------|----------|----------|
| [WSL2](./wsl2/README.md) | Windows 用户使用 WSL2 | 安装配置、网络、文件系统 |
| [Ubuntu](./ubuntu/README.md) | Linux/WSL2 Ubuntu 环境 | 系统包、常用工具 |

## 与 `agents/` 的关系

[agents/](../agents/README.md) 目录描述的是 AI Agent 的安装，而 Agent 运行在平台之上。
建议阅读顺序：**platform → runtime → agents**，即先准备好操作系统环境，再安装语言运行时，最后安装 Agent。

## 知识层说明

本目录属于**知识层**，只描述平台依赖安装方法，不决定执行顺序。
执行顺序由 [workflows/](../workflows/README.md) 中的工作流决定。

关于项目整体结构、知识层与编排层的分离规则，请参阅 [INDEX.md](../INDEX.md) 和 [RULES.md](../RULES.md)。
