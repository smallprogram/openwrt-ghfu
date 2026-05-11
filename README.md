# luci-app-ghfu (luci-app-GithubFramewareUpdate)

集成固件地址：https://github.com/smallprogram/OpenWrtAction

## 中文说明

`luci-app-ghfu` 是一个用于 OpenWrt / ImmortalWrt 的 LuCI 固件升级插件。

它的目标是让用户在路由器 Web 管理界面中，直接基于 GitHub Release 完成固件检查、下载和升级，而不需要手动复制链接或使用命令行。

### 项目作用

- 在 LuCI 页面中获取指定 GitHub 仓库的最新 Release 信息。
- 展示 Release 固件资产列表，并支持关键字筛选。
- 对比当前系统刷写时间与 Release 发布时间，给出升级结论。
- 支持下载固件并调用 `sysupgrade` 执行系统升级。
- 支持保留配置/不保留配置升级模式。
- 支持下载系统备份（与 OpenWrt 备份能力一致）。

### 核心特性

- 可配置 GitHub 仓库地址。
- 可配置获取 Release 的超时时间（默认 15 秒）。
- 升级前日志可视化（下载进度、倒计时、升级启动提示）。
- 升级过程中提供等待对话框，并在设备恢复后自动刷新页面。
- 中英文界面文案支持。

### 适用场景

- 维护自定义固件发布仓库（GitHub Release）的用户。
- 希望通过 LuCI 图形界面完成固件升级的用户。
- 需要在升级前后保留可追踪日志与状态信息的运维场景。

---

## English

`luci-app-ghfu` is a LuCI firmware upgrade app for OpenWrt / ImmortalWrt.

It allows users to check, download, and upgrade firmware directly from GitHub Releases in the router web UI, without manually handling URLs or using shell commands.

### What This Project Does

- Fetches the latest release data from a specified GitHub repository.
- Displays release assets with keyword-based filtering.
- Compares current system flash time with release publish time to provide an upgrade suggestion.
- Downloads selected firmware and triggers `sysupgrade`.
- Supports both keep-config and no-keep-config upgrade modes.
- Provides backup download support (aligned with OpenWrt backup behavior).

### Key Features

- Configurable GitHub repository input.
- Configurable release fetch timeout (default: 15 seconds).
- Visual logs for download, countdown, and upgrade trigger steps.
- Upgrade waiting dialog and auto page refresh when the device comes back online.
- Bilingual UI texts (Chinese and English).

### Typical Use Cases

- Users maintaining custom firmware releases on GitHub.
- Users who prefer upgrading firmware from LuCI instead of CLI.
- Operational workflows requiring visible status and logs around upgrades.

---

## License / 许可证

- SPDX: GPL-3.0-only
- License file: `luci-app-ghfu/LICENSE`
- Repository: https://github.com/smallprogram/luci-app-ghfu
- Copyright (C) 2026 smallprogram

This project is licensed under GNU General Public License v3.0 only.

本项目采用 GNU General Public License v3.0 only 许可证。
