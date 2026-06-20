# Go 安装指引

## 概述

Go 语言编译快速、部署简单，适合构建高效的后端服务和命令行工具。推荐使用官方二进制分发安装。

## 前提条件

- 类 Unix 操作系统（Linux / macOS / WSL2）
- `wget` 或 `curl` 可用
- `sudo` 权限（安装到系统目录时需要）

## 安装方法

### 方法一：官方二进制（推荐）

直接从 Go 官方网站下载并安装。

```bash
# 下载 Go 1.22 二进制包
wget https://go.dev/dl/go1.22.linux-amd64.tar.gz

# 解压到 /usr/local
sudo tar -C /usr/local -xzf go1.22.linux-amd64.tar.gz

# 将 Go 加入 PATH（添加到 ~/.bashrc）
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc

# 重新加载 shell 配置
source ~/.bashrc

# 清理下载文件
rm go1.22.linux-amd64.tar.gz
```

### 方法二：gvm（版本管理）

gvm（Go Version Manager）适合需要多版本切换的场景。

```bash
# 安装 gvm
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)

# 重新加载 shell 配置
source ~/.bashrc

# 安装 Go 1.22
gvm install go1.22

# 使用该版本
gvm use go1.22 --default
```

### 方法三：系统包管理器

```bash
# Ubuntu/Debian
sudo apt update && sudo apt install golang-go -y
# 注意：系统源中的 Go 版本可能较旧
```

## 验证安装

```bash
go version
# 应输出 go version go1.22.x linux/amd64
```

## 常见问题

### 1. `go` 命令找不到

确认 `/usr/local/go/bin` 在 PATH 中：

```bash
echo $PATH | grep go
export PATH=$PATH:/usr/local/go/bin
```

### 2. 版本不对（显示旧版本）

检查是否有多个 Go 安装冲突：

```bash
which go
# 确认指向正确的路径
```

### 3. GOPATH 与模块

Go 1.22 使用 Module 模式，无需设置 GOPATH：

```bash
# 但如果需要，可设置 Go 模块缓存
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

### 4. 架构不匹配

在 ARM 设备（如 Apple Silicon M 系列）上，下载 `arm64` 版本：

```bash
wget https://go.dev/dl/go1.22.linux-arm64.tar.gz
```

## 相关规则

- Go 项目推荐使用 Go Modules 管理依赖
- 使用 `gofumpt` 格式化代码，`golangci-lint` 进行静态检查
- 隐私保护规则请遵守 [RULES.md](../../RULES.md)
