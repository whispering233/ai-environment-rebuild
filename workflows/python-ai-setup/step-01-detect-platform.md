# Step 1: 检测平台

## 概述

检测当前操作系统、包管理器、系统状态，确保环境符合前置条件。

## 检测项

### 1. 检查操作系统

```bash
cat /etc/os-release
```

**期望输出**：显示操作系统名称和版本（如 Ubuntu 22.04 / 24.04 LTS）。

```bash
uname -a
```

确认是 Linux 系统（WSL2 环境下会显示 `microsoft` 或 `WSL2` 字样）。

### 2. 检查包管理器

```bash
apt --version
```

**期望输出**：显示 apt 版本号。

### 3. 检查系统更新状态

```bash
# 检查可更新的包数量
apt list --upgradable 2>/dev/null | grep -c upgradable || echo "0"
```

### 4. 检查磁盘空间

```bash
df -h / | awk 'NR==2 {print $4, "可用"}'
```

**建议**：至少 5GB 可用空间。

## 详细参考

- [Ubuntu 环境依赖](../../platform/ubuntu/README.md) — Ubuntu 基础包安装指引

## 确认事项

AI 应向用户报告检测结果：
- 操作系统类型和版本
- 包管理器状态
- 是否需要先安装基础依赖
