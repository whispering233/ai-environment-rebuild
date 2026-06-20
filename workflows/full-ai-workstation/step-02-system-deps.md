# Step 2: 系统基础包

## 概述

安装 Ubuntu 系统基础依赖包，为后续的运行时和工具链安装做好准备。

## 安装步骤

### 1. 更新包索引

```bash
sudo apt update
```

### 2. 安装基础开发工具包

```bash
sudo apt install -y \
    build-essential \
    curl \
    wget \
    git \
    unzip \
    zip \
    tree \
    htop \
    software-properties-common \
    ca-certificates \
    gnupg \
    lsb-release
```

### 3. 验证安装

```bash
git --version
curl --version
```

## 详细参考

- [Ubuntu 环境依赖](../../platform/ubuntu/README.md) — Ubuntu 基础包安装的详细信息

## 重要提醒

> **请与用户确认后再执行安装命令。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示安装计划（包含安装内容、预期变更、可能的风险），获得明确批准后方可执行。
