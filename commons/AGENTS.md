# AGENTS.md — 全局 Agents 行为控制文件

全局规则文件**无版本号，一律以源为准替换**。本仓库不维护规则副本，执行安装或更新工作流时，LLM 必须从以下 gist 拉取最新内容，作为本次会话的全局规则执行。

## 内容源

- **Gist 地址**：<https://gist.github.com/whispering233/85a8add7736d56f82d31fba049a3f8cf>
- **拉取时机**：安装工作流（`workflows/install/`）与更新工作流（`workflows/update/`）执行时
- **拉取方式**：LLM 自行拉取该 gist 内容（页面或 raw 均可），无需本地保存副本

### 拉取示例

```bash
# 拉取 gist 内容（raw 地址自动指向默认文件）
curl -fsSL https://gist.githubusercontent.com/whispering233/85a8add7736d56f82d31fba049a3f8cf/raw
```

## 说明

- 该 gist 涵盖：最高优先级指令、文档规则、计划制定规则、软件设计规则、功能开发规则、开发顺序、任务卡片切分规则、代码编写规则、UI 编写规则等
- 若 gist 内容与本仓库文档冲突，**以 gist 为准**
