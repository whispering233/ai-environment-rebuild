# Step 7: 配置并验证

## 概述

完成全局配置和全链路验证，确保整个工作站正常运行。

## 配置项

### 1. 配置 API Key

```bash
# Claude Code
echo 'export ANTHROPIC_API_KEY="your-api-key-here"' >> ~/.bashrc

# Codex CLI
echo 'export OPENAI_API_KEY="your-api-key-here"' >> ~/.bashrc

source ~/.bashrc
```

> **注意**：请将 `your-api-key-here` 替换为真实 API Key。切勿将真实 Key 写入日志或版本控制。

### 2. 配置 Shell 环境

确保 PATH 包含所有运行时和工具的 bin 目录：

```bash
# ~/.bashrc 中应包含：
export PATH="$HOME/.local/bin:$PATH"
export PATH="$(npm bin -g):$PATH"
export GOPATH=$HOME/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```

详细配置指引请参考 [Shell 配置指引](../../config/shell/README.md)。

### 3. 配置 OpenCode（如果使用）

OpenCode 配置文件位于 `~/.opencode/`，请参考 [OpenCode 配置指引](../../config/opencode/README.md)。

### 4. 安装 Skill 和 Plugin 推荐

参考以下目录获取推荐的 Skills 和 Plugins：

- [推荐 Skills](../../skills/README.md)
- [推荐 Plugins](../../plugins/README.md)

## 验证项

### 1. 验证各运行时

```bash
node --version
npm --version
python3 --version
pip3 --version
go version
```

### 2. 验证 Agent

```bash
# Claude Code
claude --version

# Codex CLI
codex --version
```

### 3. 验证 API Key 配置

```bash
echo ${ANTHROPIC_API_KEY:+ANTHROPIC_API_KEY 已配置}
echo ${OPENAI_API_KEY:+OPENAI_API_KEY 已配置}
```

### 4. 全链路测试

```bash
# Python 测试
python3 -c "print('Python OK')"

# Node.js 测试
node -e "console.log('Node.js OK')"

# Agent 测试
claude --version
```

## 详细参考

- [Shell 配置指引](../../config/shell/README.md)
- [OpenCode 配置指引](../../config/opencode/README.md)
- [推荐 Skills](../../skills/README.md)
- [推荐 Plugins](../../plugins/README.md)
- [隐私保护规则](../../RULES.md)

## 重要提醒

> **请与用户确认后再执行配置变更。**根据 [RULES.md](../../RULES.md) 的计划审批规则，AI 必须先向用户展示配置计划，获得明确批准后方可执行。
