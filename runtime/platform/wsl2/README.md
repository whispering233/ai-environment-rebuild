# WSL2

## 概述

Windows Subsystem for Linux 2 —— Windows 下的 Linux 子系统，提供完整 Linux 内核兼容性。AI Agent（Claude Code、Codex CLI 等）在 Linux 环境下表现更优。

## 安装目标

- **目标**：启用 WSL2 + 安装 Ubuntu 24.04 LTS，默认版本设为 2
- **核心命令**：管理员 PowerShell 执行 `wsl --install`（自动启用并装默认发行版）；`wsl --set-default-version 2`
- **前提**：Windows 10 2004+（19041+）或 Windows 11、BIOS 虚拟化已启用（VT-x/AMD-V）

## 来源链接

- 官方文档：<https://learn.microsoft.com/zh-cn/windows/wsl/>
- 内核更新：<https://aka.ms/wsl2kernel>

## 关键注意点

- **网络代理**：WSL2 重启后 IP 变化，勿写死代理 IP，用动态获取：`export host_ip=$(ip route | grep default | awk '{print $3}')`；Windows 防火墙需放行 WSL2 网段
- **文件系统性能**：项目代码放 WSL2 内部（`/home/...`），`/mnt/c/` 跨盘 I/O 性能差（尤其 node_modules、.git）；Windows 侧用 Remote-WSL 扩展访问
- **内存占用**：`C:\Users\<you>\.wslconfig` 设置 `memory=8GB`、`processors=4` 等上限，`wsl --shutdown` 完全重启；Vmmem 占用过高时压缩 ext4.vhdx
- **Git 换行符**：Windows/Linux 间切换时 `git config --global core.autocrlf input`，或项目根 `.gitattributes` 写 `* text=auto`
- 无法启动或报 "WSL 2 requires an update"：`wsl --update` 更新内核
