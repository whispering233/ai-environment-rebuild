# Aider 安装指引

## 概述

Aider 是一款开源的 AI 结对编程工具，支持多种 LLM 后端（OpenAI、Anthropic 等），可直接在终端中以"结对编程"模式工作，自动管理 git 提交并协调 AI 与用户的编辑。

## 前提条件

| 条件 | 说明 |
|------|------|
| Python | 版本 3.10+ |
| pip / uv | Python 包管理器 |
| Git | 版本 2.x+（Aider 依赖 Git 管理文件变更） |
| API Key | 任意兼容的 LLM API Key（OpenAI / Anthropic） |
| 终端 | Bash / Zsh（WSL2 Ubuntu 环境下建议使用 Bash） |

## 安装方法

### 方法一：pip 安装（推荐）

```bash
pip install aider-chat
```

### 方法二：uv 安装（更快速）

```bash
uv pip install aider-chat
```

> `uv` 是 Rust 实现的 Python 包管理器，比 `pip` 速度更快。安装 `uv` 请参见 [runtime/](../../runtime/README.md) 中的 Python 工具链说明。

### 方法三：pipx 安装（隔离环境）

```bash
pipx install aider-chat
```

## 分步安装指南

### 步骤 1：确认 Python 版本

```bash
python3 --version
# 应输出 Python 3.10.x 或更高版本
```

如果版本低于 3.10，请先升级 Python（参见 [runtime/](../../runtime/README.md) 中的 Python 安装指引）。

### 步骤 2：确认 Git 已安装

```bash
git --version
# 应输出 git 2.x.x
```

如果未安装 Git：

```bash
sudo apt update && sudo apt install git -y
```

### 步骤 3：安装 Aider

```bash
pip install aider-chat
```

### 步骤 4：配置 API Key

Aider 支持通过多种方式配置 API Key。推荐使用 `.env` 文件：

```bash
# 在项目目录下创建 .env 文件
echo "ANTHROPIC_API_KEY=your-api-key-here" >> .env
# 或
echo "OPENAI_API_KEY=your-api-key-here" >> .env
```

也可以使用环境变量：

```bash
export ANTHROPIC_API_KEY="your-api-key-here"
```

> **注意**：请将 `your-api-key-here` 替换为你的真实 API Key。`.env` 文件应加入 `.gitignore` 避免提交。

## 多模型支持

Aider 支持多种 LLM 后端，可通过 `--model` 参数指定：

```bash
# 使用 Claude 模型
aider --model claude-sonnet-4-20250514

# 使用 GPT-4o
aider --model gpt-4o

# 查看所有可用模型
aider --models
```

## 配置方式

- **环境变量**：`ANTHROPIC_API_KEY`、`OPENAI_API_KEY` 等
- **`.env` 文件**：在运行目录放置 `.env` 文件
- **`aider.conf.yml`**：Aider 专属配置文件（可选）
- **命令行参数**：运行时通过 `--model`、`--architect` 等参数配置

## 验证安装

```bash
aider --version
```

如输出版本号，说明安装成功。你也可以直接运行 `aider` 启动交互模式测试。

## 常见问题

### 1. 安装后 `aider` 命令找不到

确认 Python 的 bin 目录在 PATH 中：

```bash
# 查看 Python 包安装路径
python3 -m site --user-base
# 将 bin 子目录添加到 PATH
export PATH="$HOME/.local/bin:$PATH"
```

### 2. Git 未初始化

Aider 需要在 Git 仓库中工作。如果当前目录不是 Git 仓库：

```bash
git init
```

Aider 也会在首次运行时提示初始化 Git。

### 3. API Key 配置失败

Aider 启动时未检测到 API Key 会提示错误。确认：

```bash
# 检查环境变量是否已设置
echo $ANTHROPIC_API_KEY

# 检查 .env 文件是否存在
ls -la .env
```

### 4. uv 安装时依赖冲突

如果使用 `uv` 安装遇到依赖冲突，可尝试使用 `pip` 安装：

```bash
pip install aider-chat --no-deps
pip install aider-chat
```

## 相关规则

- **隐私保护**：API Key 的处理请严格遵守 [RULES.md](../../RULES.md) 中的隐私保护规则，禁止泄露到日志或版本控制。
- **计划审批**：安装前应生成计划并等待用户批准，遵循 [RULES.md](../../RULES.md) 的计划审批规则。
