# Node.js

## 概述

多数 AI Agent（Claude Code、Codex CLI、OpenCode、Pi）的核心依赖。

## 安装目标

- **版本**：22 LTS
- **方式**：nvm 管理（推荐）——
  ```bash
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash
  nvm install 22 && nvm alias default 22
  ```
- 替代：fnm（Rust 实现，更快）

## 来源链接

- nvm：<https://github.com/nvm-sh/nvm>
- fnm：<https://github.com/Schniz/fnm>
- Node.js 官网：<https://nodejs.org>

## 关键注意点

- **WSL2 路径冲突**：`which node` 应指向 `~/.nvm/versions/node/...` 而非 `/mnt/c/...`（确保用 Linux 版）
- 版本冲突：不同项目用 `.nvmrc` 按项目切换（`echo "22" > .nvmrc`）
- npm 全局包权限：配置用户级 prefix `npm config set prefix '~/.npm-global'`，并把 `~/.npm-global/bin` 加入 PATH，避免 sudo
- `nvm` 命令找不到：`source ~/.bashrc` 或手动 source `~/.nvm/nvm.sh`
