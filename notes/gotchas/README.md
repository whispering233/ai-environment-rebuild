# 常见问题与对策

本章节记录 AI 环境搭建和日常使用中频繁遇到的问题及其解决方案。

---

## 1. API Key 配置遗漏

**问题描述**：启动 AI Agent 后收到认证错误（401 Unauthorized），提示 API Key 缺失或无效。

**原因**：未设置必要的环境变量（如 `ANTHROPIC_API_KEY`、`OPENAI_API_KEY`），或 Key 未正确导出到当前 Shell 会话。

**解决方案**：

```bash
# 确认环境变量是否存在
echo $ANTHROPIC_API_KEY

# 如为空，设置环境变量
export ANTHROPIC_API_KEY="your-api-key-here"

# 添加到 Shell 配置文件以持久化
echo 'export ANTHROPIC_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

---

## 2. WSL2 网络代理问题

**问题描述**：WSL2 中无法访问外网，`curl` 或 `git clone` 超时，而 Windows 主机网络正常。

**原因**：

- WSL2 使用 NAT 网络模式，IP 会随每次重启变化
- Windows 代理未正确转发到 WSL2
- Windows 防火墙阻止了 WSL2 网段

**解决方案**：

```bash
# 在 ~/.bashrc 中使用动态 IP 获取
export host_ip=$(ip route | grep default | awk '{print $3}')
export http_proxy="http://$host_ip:7890"
export https_proxy="http://$host_ip:7890"

# Windows 防火墙需允许 WSL2 网段访问代理端口
```

---

## 3. 版本冲突（Node.js/Python）

**问题描述**：不同项目要求的 Node.js 或 Python 版本不同，全局安装导致版本冲突。

**原因**：

- 系统级安装的版本与项目要求不匹配
- 多个版本管理工具混用导致混乱
- 全局安装的包与项目依赖冲突

**解决方案**：

```bash
# Node.js：使用 nvm 按项目切换版本
nvm install 18
nvm use 18
# 在项目目录创建 .nvmrc 文件
echo "18" > .nvmrc  # 进入目录时自动切换

# Python：使用 pyenv 或虚拟环境
pyenv install 3.10
pyenv local 3.10  # 在项目目录设置局部版本
# 或使用虚拟环境
python -m venv .venv
source .venv/bin/activate
```

---

## 4. Git 换行符问题（Windows/Linux）

**问题描述**：在 Windows 和 WSL2 之间切换时，Git 报告大量文件已修改，实际仅换行符不同。

**原因**：Windows 使用 CRLF（`\r\n`）换行符，Linux 使用 LF（`\n`）换行符。

**解决方案**：

```bash
# 在 WSL2 中配置 Git 自动转换
git config --global core.autocrlf input

# 或在项目根目录创建 .gitattributes
echo "* text=auto" > .gitattributes

# 修复已有文件的换行符
git add --renormalize .
```

---

## 5. Docker 权限问题

**问题描述**：执行 `docker` 命令时收到权限拒绝错误（`permission denied`）。

**原因**：当前用户不在 `docker` 用户组中，需要 `sudo` 执行 Docker 命令。

**解决方案**：

```bash
# 将当前用户加入 docker 组
sudo usermod -aG docker $USER

# 重新登录 Shell 生效
newgrp docker

# 或在 WSL2 中重启 Docker 服务
sudo service docker restart
```

---

## 6. 磁盘空间不足

**问题描述**：开发环境运行一段时间后提示磁盘空间不足（`No space left on device`）。

**原因**：

- Docker 镜像和容器累积占用大量空间
- `node_modules` 目录膨胀
- pip/npm 缓存未清理
- WSL2 VHDX 虚拟磁盘文件自动增长不回收

**解决方案**：

```bash
# Docker 清理
docker system prune -a --volumes

# npm 缓存清理
npm cache clean --force

# pip 缓存清理
rm -rf ~/.cache/pip

# 查看磁盘占用
du -sh ~/* | sort -rh | head -20

# WSL2 磁盘压缩（Windows PowerShell 中）
# wsl --shutdown
# diskpart -> select vdisk file="C:\Users\...\ext4.vhdx" -> compact vdisk
```

---

## 7. 终端代理未生效（WSL2 重启后）

**问题描述**：WSL2 重启后终端中的代理设置不工作，`curl` 无法访问外网。

**原因**：WSL2 每次重启后 IP 地址会变化，而 Shell 配置文件中写死了旧的代理 IP。

**解决方案**：使用动态获取 IP 的方式（而非硬编码）：

```bash
# ❌ 错误写法（IP 会变）
export http_proxy="http://192.168.1.100:7890"

# ✅ 正确写法（自动获取网关 IP）
export host_ip=$(ip route | grep default | awk '{print $3}')
export http_proxy="http://$host_ip:7890"
```

---

## 8. npm 全局包找不到

**问题描述**：全局安装的 npm 包命令提示 `command not found`。

**原因**：npm 全局 bin 目录不在 `PATH` 环境变量中。

**解决方案**：

```bash
# 查看 npm 全局 bin 目录
npm bin -g

# 添加到 PATH
export PATH="$(npm bin -g):$PATH"

# 或使用 nvm 管理 Node.js（自动处理 PATH）
```

---

## 预防建议

1. **使用版本管理工具**：nvm、pyenv、gvm 等避免版本冲突
2. **定期清理**：Docker、包管理器缓存、日志文件
3. **动态配置**：避免在配置文件中硬编码 IP 等可变信息
4. **环境分离**：不同项目使用独立的虚拟环境
5. **备份配置**：关键配置文件定期备份或使用 dotfiles 管理
6. **隐私保护**：严格遵守 [RULES.md](../../RULES.md) 中的隐私保护规则，勿将真实 API Key 写入配置或日志
