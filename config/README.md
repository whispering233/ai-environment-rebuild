# Config — 配置文件指引

本子项目描述 AI 工具和 Shell 环境的配置方法与最佳实践，帮助快速搭建一致的开发环境。

## 配置项一览

| 配置项 | 配置路径 | 说明 |
|--------|----------|------|
| [OpenCode](./opencode/README.md) | ~/.opencode/ | 全局配置 |
| [Shell](./shell/README.md) | ~/.zshrc / ~/.bashrc | Shell 环境配置 |

## 隐私说明

API Key、Token 等敏感信息**不应**写入上述配置文件中。请使用 `local/` 目录或环境变量管理敏感信息。详情请参阅 [RULES.md](../RULES.md) 中的隐私保护规则。

## 知识层说明

本目录属于**知识层**，只描述配置方法，不决定执行顺序。执行顺序由 [workflows/](../workflows/README.md) 中的工作流决定。

关于项目整体结构、知识层与编排层的分离规则，请参阅 [INDEX.md](../INDEX.md) 和 [RULES.md](../RULES.md)。
