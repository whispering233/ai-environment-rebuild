# Step 3: 验证安装

## 概述

安装完成后，验证 Claude Code 是否可用。

## 验证方法

### 1. 检查版本号

```bash
claude --version
```

**期望输出**：显示 Claude Code 的版本号（如 `0.x.x`）。

如果出现 `command not found: claude`，请检查 npm 全局 bin 目录是否在 PATH 中：

```bash
# 查看 npm 全局 bin 路径
npm bin -g

# 将其添加到 PATH（例如 ~/.bashrc）
export PATH="$(npm bin -g):$PATH"
```

### 2. 测试运行

```bash
claude
```

**期望行为**：Claude Code 启动交互模式，显示欢迎信息，等待输入。

按 `Ctrl+C` 或 `Ctrl+D` 退出交互模式。

## 详细参考

- [Claude Code 安装指引](../../agents/claude-code/README.md) — 验证安装部分及常见问题
