# Python 安装指引

## 概述

Python 是众多 AI 工具和脚本的依赖（如 Aider、数据科学工具）。推荐使用 pyenv 管理多版本。

## 前提条件

- 类 Unix 操作系统（Linux / macOS / WSL2）
- 编译工具（pyenv 需要）：`build-essential`, `libssl-dev`, `zlib1g-dev` 等

## 安装方法

### 方法一：pyenv（推荐）

pyenv 允许在同一系统上安装和管理多个 Python 版本。

```bash
# 安装 pyenv
curl https://pyenv.run | bash

# 将以下内容添加到 ~/.bashrc
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# 重新加载 shell 配置
source ~/.bashrc

# 安装依赖（Ubuntu/Debian）
sudo apt update
sudo apt install build-essential libssl-dev zlib1g-dev \
  libbz2-dev libreadline-dev libsqlite3-dev curl git \
  libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev -y

# 安装 Python 3.12
pyenv install 3.12

# 设为全局默认版本
pyenv global 3.12
```

### 方法二：uv（快速替代）

uv 是 Rust 编写的 Python 包和项目管理器，速度极快。

```bash
# 安装 uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# 安装 Python 3.12
uv python install 3.12

# 设置默认版本
uv python default 3.12
```

### 方法三：系统包管理器

```bash
# Ubuntu/Debian
sudo apt update && sudo apt install python3 python3-pip python3-venv -y
```

## 验证安装

```bash
python --version
# 应输出 Python 3.12.x

pip --version
# 应输出 pip 24.x
```

## 常见问题

### 1. `pyenv install` 编译失败

确保所有编译依赖已安装。Ubuntu 下运行：

```bash
sudo apt install build-essential libssl-dev zlib1g-dev libbz2-dev \
  libreadline-dev libsqlite3-dev curl git libncursesw5-dev \
  xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

### 2. `python` 命令指向 Python 2

某些系统默认 `python` 指向 Python 2。使用 pyenv 后会自动处理。

### 3. pip 版本过旧

```bash
pip install --upgrade pip
```

### 4. 虚拟环境

推荐使用 `venv` 或 `uv venv` 创建项目隔离环境：

```bash
python -m venv .venv
source .venv/bin/activate
```

## 相关规则

- Python 包的安装应优先使用 `uv pip install` 或 `pip install`
- 系统级安装避免使用 `sudo pip`，优先使用 `--user` 标志或虚拟环境
- 隐私保护规则请遵守 [RULES.md](../../RULES.md)
