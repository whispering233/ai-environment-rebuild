# Python

## 概述

众多 AI 工具和脚本的依赖（Aider、数据科学工具）。

## 安装目标

- **版本**：3.12
- **方式**：pyenv 管理（推荐）——
  ```bash
  curl https://pyenv.run | bash
  pyenv install 3.12 && pyenv global 3.12
  ```
- 替代：uv（Rust 实现，更快）：`curl -LsSf https://astral.sh/uv/install.sh | sh && uv python install 3.12`

## 来源链接

- pyenv：<https://github.com/pyenv/pyenv>
- uv：<https://github.com/astral-sh/uv>
- Python 官网：<https://www.python.org>

## 关键注意点

- **pyenv 编译失败**：先装编译依赖 `sudo apt install build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl git libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev`
- 避免 `sudo pip`：优先虚拟环境（`python -m venv .venv`）或 `pip install --user`
- 多项目版本隔离：pyenv `pyenv local 3.10` 或虚拟环境
- 某些系统 `python` 指向 Python 2：pyenv 安装后自动处理
