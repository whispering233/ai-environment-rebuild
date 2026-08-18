# Shell

## 概述

终端环境是 AI 开发的基础，本条目覆盖 Shell 配置、PATH、别名与代理。

## 安装目标

- **版本**：Zsh + Oh-My-Zsh（推荐）或纯 Zsh
- **方式**：
  ```bash
  sudo apt install zsh -y && chsh -s $(which zsh)
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
  ```
- 推荐插件：zsh-autosuggestions、zsh-syntax-highlighting（克隆到 `$ZSH_CUSTOM/plugins/` 并在 `~/.zshrc` 启用）

## 来源链接

- Oh-My-Zsh：<https://github.com/ohmyzsh/ohmyzsh>
- Zsh：<https://www.zsh.org>

## 关键注意点

- **`.zshrc` vs `.zshenv`**：`.zshrc` 放别名/函数/提示符（交互式启动加载）；`.zshenv` 放环境变量 export（所有 Zsh 启动加载，含脚本）
- **代理**（WSL2）：勿写死 IP，动态获取 `export host_ip=$(ip route | grep default | awk '{print $3}')`
- **敏感信息**：API Key 等不要写入 Shell 配置文件，用 `source ~/.env`（不提交 git）或秘密管理工具
- 常见 PATH 补全：`~/.local/bin`、`~/.npm-global/bin`、`/usr/local/go/bin`、`$GOPATH/bin`
