# Step 3: 安装 Node.js

## 概述

安装 Node.js 运行时环境，为 Claude Code、Codex CLI 等 AI Agent 提供运行基础。

## 安装步骤

### 1. 检查是否已安装

```bash
node --version
npm --version
```

### 2. 通过 NodeSource 安装 Node.js 20 LTS（推荐）

```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
```

### 3. 验证安装

```bash
node --version
npm --version
```

### 4. 配置 npm（可选）

设置 npm 镜像源以加速下载：

```bash
npm config set registry https://registry.npmmirror.com
```

## 详细参考

- [Node.js 安装指引](../../runtime/node-js/README.md) — 详细的 Node.js 安装选项和常见问题

## 重要提醒

> **请与用户确认后再执行安装命令。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示安装计划（包含安装内容、预期变更、可能的风险），获得明确批准后方可执行。
