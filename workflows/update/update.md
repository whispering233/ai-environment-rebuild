# 通用更新 — Update

## 适用场景

更新已安装的 Agents、运行时/工具，以及 commons 通用内容。

## 核心流程

```
检测现状 → 确定更新对象 → 对照来源链接 → 生成计划 → 用户审批 → 执行 → 验证
```

### 步骤 1：拉取全局规则

按 [commons/AGENTS.md](../../commons/AGENTS.md) 从 gist 拉取全局规则，作为本次会话约束。

### 步骤 2：检测与确认更新对象

询问用户要更新哪些，并检测现状：

- **Agents**：`claude --version`、`codex --version`、`aider --version` 等（见各 `agents/<tool>/README.md`）
- **Runtime**：`node --version`、`python --version`、`go version` 等
- **commons**：`commons/AGENTS.md`（全局规则）、`commons/skills.md`、`commons/plugins.md`

### 步骤 3：生成计划并审批

计划包含：更新对象、更新方式、预期变更、风险（如破坏性升级、依赖不兼容）。提交用户审批。

### 步骤 4：执行更新

| 更新对象 | 更新方式 |
|----------|----------|
| Agents | 各 `agents/<tool>/README.md` 的"更新"章节（如 `npm update -g @anthropic-ai/claude-code`） |
| Runtime | 各 `runtime/<分类>/<软件>/README.md` 的更新方式（版本管理工具升级） |
| commons/AGENTS.md | **一律替换，无版本号**：从 gist（<https://gist.github.com/whispering233/85a8add7736d56f82d31fba049a3f8cf>）拉取最新内容覆盖 |
| commons/skills.md / plugins.md | **LLM 对照清单中的来源链接自行判断**是否需要更新（拉取链接核实版本/内容） |

### 步骤 5：验证

- Agents / Runtime：`--version` 确认版本已更新
- commons/AGENTS.md：确认内容与 gist 一致
