# Tailscale 一键安装与自维护脚本

**作者**：胡博涵  
**版本**：v1.2（2025 智能时区增强版）  
**仓库**：[husibo16/Tailscale](https://github.com/husibo16/Tailscale)

---

## 简介

本脚本用于在 Debian / Ubuntu 系统上，自动安装、配置 Tailscale 并设置每日自动维护。  
通过 `systemd timer` 实现定时重启与自检，确保节点长期稳定在线。  

---

## 主要特性

- ✅ 自动识别系统版本（Debian / Ubuntu 全系列）  
- 🌐 自动添加官方软件源并安装最新版 Tailscale  
- 🧭 智能检测系统时区（如 Asia/Shanghai）  
- ⏰ 每日定时重启 tailscaled 服务，防止连接异常  
- 🧾 自动生成日志并设置轮换策略（`/var/log/tailscale_*.log`）  
- 🔄 支持断网/宕机后自动补跑定时任务  
- 🚀 首次执行后自动授权、自检、日志初始化  

---

## 系统要求

| 项目     | 要求                       |
|----------|----------------------------|
| 操作系统 | Debian 11+ 或 Ubuntu 20.04+|
| 权限     | 需要 root 或 sudo 权限      |
| 网络     | 能访问 https://pkgs.tailscale.com |

---

## 快速安装

```bash
curl -fsSL <脚本URL> | bash
