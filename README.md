## 🌀 Tailscale 一键安装与自维护脚本

📘 项目简介

本脚本用于 在 Debian / Ubuntu 系统上自动安装与自维护 Tailscale
，
并通过 systemd 实现 每日定时自检与自动重启 tailscaled 服务，确保节点长期稳定在线。

主要特性：

✅ 自动识别系统版本（Debian / Ubuntu 全系列）

🌐 自动添加官方软件源并安装最新版 Tailscale

🧠 智能检测系统时区（Asia/Shanghai 等）

🔁 每日定时重启 tailscaled，防止连接异常

🧾 自动生成与轮换日志（/var/log/tailscale_*.log）

⚙️ 支持断网恢复、宕机后自动补跑定时任务

🚀 首次执行后自动完成授权、自检与日志初始化
