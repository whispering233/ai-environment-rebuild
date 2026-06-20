# Step 2: 安装 Python

## 概述

安装 Python 运行时环境，包括 Python 解释器、pip 包管理器、pyenv 版本管理工具。

## 安装步骤

### 1. 检查是否已安装 Python

```bash
python3 --version
pip3 --version
```

如果已安装且版本满足需求（Python 3.10+），可跳过安装步骤。

### 2. 通过 apt 安装 Python（推荐）

```bash
sudo apt update
sudo apt install -y python3 python3-pip python3-venv
```

### 3. 安装 pyenv（可选，用于管理多 Python 版本）

```bash
curl https://pyenv.run | bash
```

安装后按提示将 pyenv 添加到 shell 配置文件：

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

### 4. 验证安装

```bash
python3 --version
pip3 --version
```

## 详细参考

- [Python 安装指引](../../runtime/python/README.md) — 详细的 Python 安装选项和常见问题

## 重要提醒

> **请与用户确认后再执行安装命令。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示安装计划（包含安装内容、预期变更、可能的风险），获得明确批准后方可执行。
