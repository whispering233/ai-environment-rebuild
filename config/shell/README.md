# Shell 配置指引

## 概述

Shell 环境是 AI 开发的基础。本指南介绍如何配置 Shell 以获得最佳的 AI 开发体验。

## 推荐配置

### Zsh + Oh-My-Zsh（推荐）

```bash
# 安装 Zsh
sudo apt install zsh -y

# 将 Zsh 设为默认 Shell
chsh -s $(which zsh)

# 安装 Oh-My-Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 安装推荐插件
git clone https://github.com/zsh-users/zsh-autosuggestions.git \
  $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

在 `~/.zshrc` 中启用插件：

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

### 纯 Zsh 配置（轻量）

如不需要 Oh-My-Zsh，可手动配置：

```bash
# 安装 Zsh
sudo apt install zsh -y

# 使用 Prezto 或自行配置 prompts/completions
```

## 必要别名和导出

### 开发工具 PATH

```bash
# ~/.bashrc 或 ~/.zshrc

# Go
export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin

# Node.js (nvm 会自动设置)
# Python (pyenv 会自动设置)

# 本地二进制
export PATH=$HOME/.local/bin:$PATH

# npm 全局包
export PATH=$HOME/.npm-global/bin:$PATH
```

### 常用别名

```bash
# 开发相关
alias dev-update='sudo apt update && sudo apt upgrade -y'
alias cls='clear'
alias la='ls -la'
alias ll='ls -lh'

# Git
alias gst='git status'
alias gco='git checkout'
alias gcb='git checkout -b'
alias gcm='git commit -m'
alias glog='git log --oneline --graph --decorate -20'

# Docker
alias dk='docker'
alias dkc='docker compose'
```

### 代理配置（WSL2 环境）

```bash
# 动态获取 Windows 主机 IP（WSL2）
export host_ip=$(ip route | grep default | awk '{print $3}')
export http_proxy="http://$host_ip:7890"
export https_proxy="http://$host_ip:7890"
```

## .zshrc vs .zshenv 区别

| 文件 | 加载时机 | 用途 |
|------|----------|------|
| `.zshrc` | 交互式 Shell 启动时 | 别名、函数、提示符、补全 |
| `.zshenv` | 所有 Zsh 启动时（含脚本） | 环境变量、PATH |

建议：

- **`~/.zshrc`**：放置别名、函数、提示符配置、补全设置
- **`~/.zshenv`**：放置 `export` 环境变量（如 `PATH`、`EDITOR`）
- **`~/.zprofile`**：登录 Shell 执行的命令（如启动代理）

## 环境变量管理

### 推荐做法

```bash
# ~/.zshenv — 跨会话通用的环境变量
export EDITOR=vim
export VISUAL=vim
export PAGER=less

# ~/.zshrc — 交互式配置
export LANG=zh_CN.UTF-8
export LC_ALL=zh_CN.UTF-8
```

### 敏感信息

API Key 等敏感信息**不要**直接写入 Shell 配置文件。可使用：

```bash
# 源自 .env 文件（不提交到 Git）
source ~/.env
```

或使用专门的秘密管理工具。

## 相关参考

- [Oh-My-Zsh 官方文档](https://ohmyz.sh/)
- [OpenCode 配置](../opencode/README.md)
- 本项目的 [RULES.md](../../RULES.md) 中的隐私保护规则
