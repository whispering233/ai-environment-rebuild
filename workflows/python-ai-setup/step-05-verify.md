# Step 5: 验证完整链路

## 概述

验证 Python 环境、AI Agent 及完整工作链路是否正常运行。

## 验证项

### 1. 验证 Python

```bash
python3 --version
pip3 --version
```

**期望输出**：显示 Python 3.10+ 和 pip 版本号。

### 2. 验证 Agent

**Claude Code：**

```bash
claude --version
```

**Codex CLI：**

```bash
codex --version
```

**Aider：**

```bash
aider --version
```

### 3. 验证 API Key 配置

```bash
# Claude Code
echo ${ANTHROPIC_API_KEY:+ANTHROPIC_API_KEY 已配置}
# 仅显示 "已配置"，不泄露 Key 内容

# Codex CLI
echo ${OPENAI_API_KEY:+OPENAI_API_KEY 已配置}
```

### 4. 测试完整链路

运行 Agent 测试是否可正常启动：

```bash
# Claude Code（交互模式，确认后退出）
claude
```

## 详细参考

- [Python 安装指引](../../runtime/python/README.md)
- [Claude Code 安装指引](../../agents/claude-code/README.md)
- [Codex CLI 安装指引](../../agents/codex-cli/README.md)

## 故障排查

如果验证失败，请按照以下顺序排查：

1. 检查各组件是否已正确安装（重新运行版本检查命令）
2. 检查 API Key 是否正确设置
3. 检查 PATH 是否包含可执行文件路径
4. 查阅对应知识文件中的"常见问题"部分
