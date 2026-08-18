# Ubuntu

## 概述

AI 开发环境最常用的 Linux 发行版，覆盖 WSL2 Ubuntu 与原生 Ubuntu。

## 安装目标

- **版本**：22.04 LTS 或 24.04 LTS
- **基础包**（AI 开发必需）：
  ```bash
  sudo apt install -y build-essential curl wget git unzip zip tar gpg \
    lsb-release software-properties-common apt-transport-https ca-certificates jq tree htop tmux
  ```
- **Docker（可选）**：`curl -fsSL https://get.docker.com | sudo sh`，随后 `sudo usermod -aG docker $USER`

## 来源链接

- 官方文档：<https://help.ubuntu.com/>
- Docker 安装脚本：<https://get.docker.com>

## 关键注意点

- **apt 慢/失败**：国内网络可换镜像源（备份 sources.list 后 sed 替换 archive.ubuntu.com → mirrors.ustc.edu.cn）
- **Docker 权限**：`Got permission denied` → 用户加入 docker 组后重新登录（`newgrp docker`）
- WSL2 长时间休眠后时间不同步：`sudo hwclock -s`（可加 ~/.bashrc 自动执行）
- 模型下载/编译可能撑爆 `/tmp`：关注 `df -h /tmp`
