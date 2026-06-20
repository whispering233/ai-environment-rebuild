# Step 5: 安装 Go

## 概述

安装 Go 语言运行时环境。

## 安装步骤

### 1. 检查是否已安装

```bash
go version
```

### 2. 通过 apt 安装 Go

```bash
sudo apt update
sudo apt install -y golang-go
```

> **注意**：apt 仓库中的 Go 版本可能较旧。如需最新版本，建议从 [golang.org](https://go.dev/dl/) 下载官方二进制包。

### 3. 验证安装

```bash
go version
```

### 4. 配置 Go 环境变量

确保以下环境变量已设置：

```bash
export GOPATH=$HOME/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```

添加到 shell 配置文件以持久生效：

```bash
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
echo 'export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin' >> ~/.bashrc
source ~/.bashrc
```

## 详细参考

- [Go 安装指引](../../runtime/golang/README.md) — 详细的 Go 安装选项和常见问题

## 重要提醒

> **请与用户确认后再执行安装命令。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示安装计划（包含安装内容、预期变更、可能的风险），获得明确批准后方可执行。
