# Node.js 安装指引

## 概述

Node.js 是 AI Agent（Claude Code、Codex CLI）的核心依赖。推荐使用版本管理工具安装，便于切换版本。

## 前提条件

- 类 Unix 操作系统（Linux / macOS / WSL2）
- `curl` 或 `wget` 可用
- `git`（部分工具需要）

## 安装方法

### 方法一：nvm（推荐）

nvm（Node Version Manager）是最常用的 Node.js 版本管理器。

```bash
# 安装 nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash

# 重新加载 shell 配置
source ~/.bashrc

# 安装 Node.js 22 LTS
nvm install 22

# 使用该版本
nvm use 22

# 设为默认版本
nvm alias default 22
```

### 方法二：fnm（快速替代）

fnm（Fast Node Manager）使用 Rust 编写，性能更优。

```bash
# 使用安装脚本
curl -fsSL https://fnm.vercel.app/install | bash

# 重新加载 shell 配置
source ~/.bashrc

# 安装并使用 Node.js 22
fnm install 22
fnm use 22
fnm default 22
```

### 方法三：系统包管理器

不推荐，版本可能过旧：

```bash
# Ubuntu/Debian
sudo apt update && sudo apt install nodejs npm -y
```

## 验证安装

```bash
node --version
# 应输出 v22.x.x

npm --version
# 应输出 10.x.x 或更高版本
```

## 常见问题

### 1. `nvm` 命令找不到

重新加载 shell 配置文件：

```bash
source ~/.bashrc
```

或检查 `~/.nvm/nvm.sh` 是否存在并手动 source。

### 2. 权限错误（EACCES）

使用 nvm 安装 Node.js 可避免 sudo 需求。如已使用系统包管理器安装，建议卸载后改用 nvm。

### 3. WSL2 路径冲突

WSL2 环境下确保使用的是 Linux 版 Node.js，而非 Windows 版：

```bash
which node
# 应返回 /home/yourname/.nvm/versions/node/... 而非 /mnt/c/...
```

### 4. npm 全局包权限

```bash
# 配置 npm 全局安装路径到用户目录
npm config set prefix '~/.npm-global'
mkdir -p ~/.npm-global
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
```

## 相关规则

- Agent 安装前请先确认 Node.js 版本满足要求（参见各 Agent 安装指引）
- 隐私保护规则请遵守 [RULES.md](../../RULES.md)
