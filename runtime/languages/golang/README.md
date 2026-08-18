# Go

## 概述

编译快速、部署简单，适合后端服务和命令行工具。

## 安装目标

- **版本**：1.22+
- **方式**：官方二进制（推荐）——
  ```bash
  wget https://go.dev/dl/go1.22.linux-amd64.tar.gz
  sudo tar -C /usr/local -xzf go1.22.linux-amd64.tar.gz
  echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
  ```
- 替代：gvm（多版本切换）

## 来源链接

- 官方下载：<https://go.dev/dl/>
- gvm：<https://github.com/moovweb/gvm>

## 关键注意点

- **ARM 设备**（Apple Silicon 等）：下载 `arm64` 版本（`go1.22.linux-arm64.tar.gz`）
- `go` 命令找不到：确认 `/usr/local/go/bin` 在 PATH；多版本冲突时 `which go` 排查
- Go Modules 模式无需设置 GOPATH；如需可 `export GOPATH=$HOME/go` 并加入 PATH
