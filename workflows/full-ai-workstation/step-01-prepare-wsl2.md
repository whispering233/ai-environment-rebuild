# Step 1: WSL2 配置

## 概述

在 Windows 11 上配置 WSL2 环境，为后续安装做好准备。

## 检查项

### 1. 确认 WSL2 已启用

在 Windows PowerShell（管理员）中运行：

```powershell
wsl --status
```

**期望输出**：显示 WSL 版本为 2，以及默认发行版信息。

### 2. 检查 WSL 版本

```powershell
wsl -l -v
```

**期望输出**：列出已安装的 Linux 发行版及其 WSL 版本（应显示 v2）。

### 3. 确认 Ubuntu 发行版

```powershell
wsl -l
```

**期望输出**：显示 `Ubuntu` 或 `Ubuntu-24.04` 等发行版名称。

### 4. 检查 WSL2 资源配置

WSL2 默认内存和 CPU 配置可能不足以运行 AI 工具链。建议在 Windows 用户目录下创建 `.wslconfig` 文件：

```
[wsl2]
memory=8GB
processors=4
localhostForwarding=true
```

> **注意**：修改 `.wslconfig` 后需执行 `wsl --shutdown` 并重新启动 WSL2 生效。

## 详细参考

- [WSL2 平台依赖](../../platform/wsl2/README.md) — WSL2 安装和配置的详细信息

## 重要提醒

> **请与用户确认后再执行配置变更。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示配置计划，获得明确批准后方可执行。
