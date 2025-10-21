# 🌀 Tailscale 一键安装与自维护脚本

**作者**：胡博涵  
**版本**：v1.2（2025 智能时区增强版）  
**仓库**：[husibo16/Tailscale](https://github.com/husibo16/Tailscale)

---

## 📘 简介

本脚本用于在 **Debian / Ubuntu 系统** 上自动安装与配置 [Tailscale](https://tailscale.com)，  
并通过 `systemd timer` 实现每日定时重启与自检，确保节点长期稳定在线。  

适用于服务器、树莓派、VPS 等需要长期保持连接的场景。

---

## ✨ 主要特性

- ✅ 自动识别系统版本（Debian / Ubuntu 全系列）  
- 🌐 自动添加官方软件源并安装最新版 Tailscale  
- 🧭 智能检测系统时区（如 Asia/Shanghai）  
- ⏰ 每日 03:00 自动重启 tailscaled 服务，防止连接异常  
- 🧾 自动生成日志并启用 logrotate 轮换策略（`/var/log/tailscale_*.log`）  
- 🔄 支持断网/宕机后自动补跑任务  
- 🚀 首次执行自动完成授权、自检、日志初始化  
- 🧠 稳定可长期运行（生产环境可用）  

---

## 🧰 系统要求

| 项目       | 要求                                     |
|------------|------------------------------------------|
| 操作系统   | Debian 11+ / Ubuntu 20.04+               |
| 权限       | root 或具备 sudo 权限                    |
| 网络       | 可访问 `https://pkgs.tailscale.com`      |
| 初始化工具 | systemd（用于维护任务定时器）             |

---

## ⚙️ 快速安装

### 一键安装（推荐）

```bash
curl -fsSL https://raw.githubusercontent.com/husibo16/Tailscale/main/install-tailscale.sh | bash
```

## 🔧 常用命令
```bash
# 查看 tailscaled 状态
systemctl status tailscaled --no-pager

# 手动运行维护任务
bash /usr/local/bin/tailscale-maintenance.sh

# 查看维护日志
cat /var/log/tailscale_maintenance.log

# 检查定时任务
systemctl list-timers | grep tailscale

# 手动重启 tailscaled
systemctl restart tailscaled
```
## 🧾 卸载与清理

systemctl disable --now tailscale-maintenance.timer tailscaled
apt remove --purge tailscale -y
rm -f /etc/apt/sources.list.d/tailscale.list
rm -f /usr/share/keyrings/tailscale-archive-keyring.gpg
rm -f /usr/local/bin/tailscale-maintenance.sh
rm -f /etc/systemd/system/tailscale-maintenance.{service,timer}
rm -f /etc/logrotate.d/tailscale-maintenance
rm -f /var/log/tailscale_*.log

