# luci-app-ghfu (luci-app-GithubFramewareUpdate)

集成固件地址：https://github.com/smallprogram/OpenWrtAction

![alt text](img/cn.png)

![alt text](img/update.png)

### install apk
```
# install apk
apk add --allow-untrusted --repositories-file /dev/null /tmp/luci-app-ghfu-xxxx.apk
apk add --allow-untrusted --repositories-file /dev/null /tmp/luci-i18n-ghfu-zh-cn-xxxx.apk
```
### feeds compile
```
# add to feeds
src-git ghfu https://github.com/smallprogram/luci-app-ghfu.git;main

# update and install feeds
./scripts/feeds update ghfu && ./scripts/feeds install -a -p ghfu

# compile ghfu
make package/feeds/ghfu/luci-app-ghfu/compile -j$(nproc)
```

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
- 支持单独保存基础配置（GitHub 仓库、获取超时、保留配置升级）。
- 升级前日志可视化（下载进度、倒计时、升级启动提示）。
- 升级过程中提供等待对话框，并在设备恢复后自动刷新页面。
- 获取到最新 Release 后，会尝试根据上次升级固件名自动筛选并自动选中可升级固件。
- 升级业务进行中会锁定关键按钮（保存基础配置、保存过滤规则、获取最新 Release、下载备份、下载并升级系统），异常退出后自动恢复。
- 中英文界面文案支持。

### 自动筛选规则（Release/固件）

- 未获取到 Release 信息：不进行自动筛选。
- 获取到 Release 信息后：
	- 若 Release/固件 输入框中为 `Release名称 / 固件文件名`，会提取最后的固件文件名用于模糊筛选。
	- 若筛选结果唯一：自动选中该固件，并记录日志：已自动筛选为上次更新的固件名xxx，如果需要更改请删除模糊检索内容。
	- 若筛选结果为 0 条或多条：记录日志：最新release中没有固件名称xxx，请手动筛选或等待下次仓库编译。并清空模糊检索框，交由用户手动筛选。

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
