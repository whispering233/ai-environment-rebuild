# WSL2 环境配置指引

## 概述

Windows Subsystem for Linux 2 (WSL2) 是 Windows 下的 Linux 子系统，提供完整的 Linux 内核兼容性。
本指南帮助 Windows 用户搭建 AI 开发环境。

### 适用场景

- Windows 用户需要运行 Linux 原生开发工具
- AI Agent（如 Claude Code、Codex CLI）在 Linux 环境下表现更优
- 需要 Docker 容器支持（WSL2 后端）
- 需要 Linux 文件系统和命令行生态

## 前置检查

在开始安装前，请确认以下条件：

1. **Windows 版本**：Windows 10 版本 2004+（内部版本 19041+）或 Windows 11
   - 按 `Win + R` → 输入 `winver` 确认版本
2. **BIOS 虚拟化**：确保 BIOS 中已启用虚拟化技术（VT-x/AMD-V）
   - 任务管理器 → 性能 → CPU → "虚拟化：已启用"
3. **管理员权限**：安装过程需要管理员权限

## 安装步骤

### 1. 启用 WSL2

以**管理员身份**打开 PowerShell 或 CMD，执行：

```powershell
wsl --install
```

> 该命令会自动启用 WSL 功能并安装默认的 Ubuntu 发行版。

如果 `wsl --install` 不可用，可手动启用：

```powershell
# 启用 WSL 功能
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# 启用虚拟机平台
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# 重启后继续
```

### 2. 设置默认版本为 WSL2

```powershell
wsl --set-default-version 2
```

### 3. 安装 Ubuntu 发行版

通过 Microsoft Store 安装 "Ubuntu 24.04 LTS"（推荐），或使用命令行：

```powershell
wsl --install -d Ubuntu-24.04
```

### 4. 确认安装

```powershell
wsl -l -v
```

输出示例：

```
  NAME            STATE           VERSION
* Ubuntu-24.04    Running         2
```

## 网络配置

### 代理设置

WSL2 的网络与 Windows 主机共享。如果 Windows 主机使用代理，需要在 WSL2 中配置：

```bash
# 在 WSL2 的 ~/.bashrc 或 ~/.zshrc 中添加
# 获取 Windows 主机 IP（WSL2 的默认网关）
export host_ip=$(ip route | grep default | awk '{print $3}')
export http_proxy="http://$host_ip:7890"
export https_proxy="http://$host_ip:7890"
export all_proxy="http://$host_ip:7890"
```

> 注意：代理端口（如 7890）需根据实际代理软件调整。Windows 防火墙需允许 WSL2 网段访问。

### DNS 配置

如果遇到 DNS 解析问题，可在 `/etc/wsl.conf` 中配置：

```ini
[network]
generateResolvConf = false
```

然后手动创建 `/etc/resolv.conf`：

```bash
nameserver 8.8.8.8
nameserver 1.1.1.1
```

## 文件系统注意事项

### 跨 OS 文件性能

- **Linux 文件系统（推荐）**：将项目代码存放在 WSL2 内部（如 `/home/yourname/projects/`），性能最佳
- **Windows 文件系统（性能差）**：通过 `/mnt/c/` 访问 Windows 文件，I/O 性能显著下降（尤其是 `node_modules`、`.git` 等大量小文件操作）
- **不要**：在 Windows 侧用 IDE 直接打开 WSL2 内部的文件（使用 `wsl://` 或 Remote-WSL 扩展）

### 路径互访

| 方向 | 路径示例 |
|------|----------|
| WSL2 → Windows | `/mnt/c/Users/yourname/` |
| Windows → WSL2 | `\\\\wsl.localhost\\Ubuntu-24.04\\home\\yourname\\` |

## 推荐配置

### 内存限制

默认 WSL2 可使用所有主机内存。建议限制以防止占用过高：

在 Windows 用户目录下创建 `.wslconfig`（`C:\Users\yourname\.wslconfig`）：

```ini
[wsl2]
memory=8GB
processors=4
swap=2GB
localhostForwarding=true
```

> 修改后需重启 WSL2：`wsl --shutdown` 再重新启动。

### 推荐的 WSL2 配置（`/etc/wsl.conf`）

```ini
[automount]
enabled = true
options = "metadata,umask=22,fmask=11"
mountFsTab = true

[network]
hostname = dev-wsl
generateResolvConf = true

[interop]
enabled = true
appendWindowsPath = true
```

## 常见问题

### Q1: WSL2 无法启动或报错 "WSL 2 requires an update"

**原因**：内核组件未更新。
**解决**：
```powershell
# 更新 WSL2 Linux 内核
wsl --update
# 或手动下载安装：
# https://aka.ms/wsl2kernel
```

### Q2: 从 Windows 访问 WSL2 服务（如开发服务器）

WSL2 的 IP 会随重启变化。推荐：
- 使用 `localhost`：WSL2 默认将端口转发到 Windows 的 `localhost`
- 或使用 `wsl hostname -I` 获取当前 IP
- 配置 `.wslconfig` 中的 `localhostForwarding=true`

### Q3: Vmmem 进程内存占用过高

**原因**：WSL2 内存回收不及时。
**解决**：
- 配置 `.wslconfig` 中的 `memory` 上限
- 使用 `wsl --shutdown` 完全重启
- 或使用 `sudo sysctl -w vm.drop_caches=3` 手动释放缓存

### Q4: 网络代理在 WSL2 中不生效

**原因**：WSL2 重启后 Windows IP 变化。
**解决**：不要在 shell 配置中写死 IP，使用动态获取方式：

```bash
export host_ip=$(ip route | grep default | awk '{print $3}')
```

## 参考

- [WSL2 官方文档](https://learn.microsoft.com/zh-cn/windows/wsl/)
- [WSL2 内核更新](https://aka.ms/wsl2kernel)
- 本项目的 [RULES.md](../../RULES.md) 中的隐私保护规则
