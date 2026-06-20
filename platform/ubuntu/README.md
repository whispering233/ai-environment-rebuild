# Ubuntu 环境配置指引

## 概述

Ubuntu 是 AI 开发环境中最常用的 Linux 发行版。本指南覆盖 WSL2 Ubuntu 和原生 Ubuntu 环境的基础依赖安装。

### 适用场景

- WSL2 Ubuntu（Windows 下的 Linux 子系统）
- 原生 Ubuntu 桌面/服务器
- 基于 Ubuntu 的衍生发行版（如 Pop!_OS、Linux Mint）

## 前置检查

### 确认 Ubuntu 版本

```bash
lsb_release -a
# 或
cat /etc/os-release
```

推荐版本：**Ubuntu 22.04 LTS** 或 **24.04 LTS**（当前最新 LTS）。

### 更新现有包

```bash
sudo apt update && sudo apt upgrade -y
```

## 基础包安装

以下为 AI 开发环境必需的基础包：

```bash
sudo apt install -y \
  build-essential \
  curl \
  wget \
  git \
  unzip \
  zip \
  tar \
  gpg \
  lsb-release \
  software-properties-common \
  apt-transport-https \
  ca-certificates \
  gnupg \
  jq \
  tree \
  htop \
  tmux
```

### 包说明

| 包名 | 用途 |
|------|------|
| `build-essential` | 编译工具链（gcc, g++, make） |
| `curl` / `wget` | 网络请求、下载 |
| `git` | 版本控制 |
| `unzip` / `zip` / `tar` | 压缩解压 |
| `gpg` / `ca-certificates` | 安全认证、包签名验证 |
| `software-properties-common` | PPA 管理 |
| `jq` | JSON 命令行处理 |
| `tree` | 目录树查看 |
| `htop` | 系统资源监控 |
| `tmux` | 终端复用器 |

## 开发工具链

### Docker

AI Agent 开发中 Docker 用于环境隔离和容器化部署。

```bash
# 官方推荐方式
curl -fsSL https://get.docker.com | sudo sh

# 将当前用户加入 docker 组（避免每次 sudo）
sudo usermod -aG docker $USER
# 重新登录或 newgrp docker 生效
```

验证：

```bash
docker --version
docker run hello-world
```

### 编译工具

```bash
# 完整编译工具链（若未通过 build-essential 安装）
sudo apt install -y gcc g++ make cmake

# 性能分析工具
sudo apt install -y perf-tools-unstable linux-tools-common
```

## Shell 环境

### Zsh

```bash
sudo apt install -y zsh

# 安装 Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 切换默认 Shell
chsh -s $(which zsh)
```

### Fish

```bash
sudo apt install -y fish

# 切换默认 Shell
chsh -s $(which fish)
```

> 切换默认 Shell 后需重新登录生效。

## 包管理配置

### APT 国内镜像（可选）

在 WSL2 或中国大陆网络环境下，建议配置国内镜像源以加速包下载：

```bash
# 备份原配置
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

# Ubuntu 24.04 (Noble) 示例 — 根据实际版本修改
sudo sed -i 's|archive.ubuntu.com|mirrors.ustc.edu.cn|g' /etc/apt/sources.list
sudo sed -i 's|security.ubuntu.com|mirrors.ustc.edu.cn|g' /etc/apt/sources.list

sudo apt update
```

### PPA 使用

```bash
# 添加 PPA
sudo add-apt-repository ppa:deadsnakes/ppa  # Python 多版本
sudo apt update
```

## 环境检验清单

安装完成后，建议逐项确认：

```bash
# 系统
uname -a              # 内核版本
lsb_release -a        # 发行版版本

# 基础工具
gcc --version         # C 编译器
git --version         # Git
curl --version        # Curl
docker --version      # Docker

# Shell
echo $SHELL           # 当前 Shell
zsh --version         # Zsh 版本（如安装）
fish --version        # Fish 版本（如安装）
```

## 常见问题

### Q1: `sudo apt update` 很慢或失败

**原因**：默认源在国内网络环境下载缓慢。
**解决**：切换到国内镜像源（见上方 "APT 国内镜像"）。

### Q2: Docker 安装后权限不足

```bash
# 错误：Got permission denied while trying to connect to Docker daemon
```

**解决**：
```bash
sudo usermod -aG docker $USER
# 然后重新登录或执行：newgrp docker
```

### Q3: WSL2 Ubuntu 时间不同步

```bash
# WSL2 长时间休眠后可能出现时间偏差
sudo hwclock -s
```

建议在 `~/.bashrc` 中添加：
```bash
# WSL2 时间同步
if grep -q WSL2 /proc/version 2>/dev/null; then
    sudo hwclock -s 2>/dev/null || true
fi
```

### Q4: `/tmp` 空间不足

某些 AI 工具（如模型下载、编译）会使用 `/tmp`。
```bash
# 查看临时目录使用情况
df -h /tmp

# 可挂载到更大分区（如需）
# sudo mount --bind /home/user/tmp /tmp
```

## 参考

- [Ubuntu 官方文档](https://help.ubuntu.com/)
- [WSL2 配置指引](../wsl2/README.md)（Windows 用户请先阅读）
- 本项目的 [RULES.md](../../RULES.md) 中的全局规则
