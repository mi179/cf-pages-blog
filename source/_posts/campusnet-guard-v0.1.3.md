---
title: CampusNet Guard v0.1.3 — 校园网自动认证与断网重连工具
date: 2026-06-10 10:00:00
tags:
  - campusnet
  - 校园网
  - 开源
  - python
---

## 为什么做这个工具

宿舍电脑、NAS、实验室工位机，这些设备需要一直保持校园网在线。但校园网每隔一段时间就会断开认证，手动重新登录很烦。

CampusNet Guard 就是为了解决这个问题：自动检测断网，自动重新认证，7x24 无感守护。

## 适合谁

- **宿舍电脑**：笔记本、台式机，断网自动重连
- **NAS / 软路由 / 小主机**：7x24 在线，不希望手动登录
- **实验室 / 办公室工位**：保持校园网在线
- **机房设备**：批量设备长期在线

## Windows 使用

1. 从 [GitHub Releases](https://github.com/mi179/campusnet-guard/releases/latest) 下载 `campusnet-guard-windows.zip`
2. 解压，双击 `campusnet-guard-gui.exe`
3. 打开"高级"页，点击"添加账号"，填写运营商、学号、密码
4. 回到"主页"，点击"开始守护"
5. 可选：打开"设置"页，勾选"开机后自动运行并守护校园网"

不需要安装 Python，不需要命令行。

> 当前版本暂未进行代码签名，Windows SmartScreen 可能提示未知发布者。请只从官方 GitHub Releases 下载，并自行判断是否信任。

## Linux 使用

通过源码安装，使用命令行：

```bash
git clone https://github.com/mi179/campusnet-guard.git
cd campusnet-guard
bash scripts/linux/install.sh
source .venv/bin/activate
campusnet setup
campusnet start
```

可配合 tmux/screen 后台运行，适合 NAS、软路由、小主机等场景。

## 密码安全

- Windows 使用 DPAPI 保护密码，绑定当前系统用户
- Linux 使用本地密钥保护密码，配置文件权限 600
- 不收集任何遥测、日志、密码、cookie、token

## v0.1.3 更新

- 修复了云端打包和发布流程
- 公开文档措辞统一
- Release 资产命名统一为 CampusNet Guard 品牌
- 新增官网和国内备用下载入口

## 下载

- **主下载**：[GitHub Releases](https://github.com/mi179/campusnet-guard/releases/latest)
- **官网**：[campusnet.journeymind.blog](https://campusnet.journeymind.blog)
- **国内备用下载**：见官网或项目文档

## 免责声明

- 本工具仅用于用户自己的校园网账号自动认证和断网重连
- 不绕过认证、不破解、不共享账号、不突破在线数量限制
- 学校/运营商的认证策略由网络系统决定
- 不保证适配所有 Ruijie ePortal 版本
- 使用者应遵守学校网络管理规定

## 链接

- **GitHub 仓库**：https://github.com/mi179/campusnet-guard
- **最新 Release**：https://github.com/mi179/campusnet-guard/releases/latest
- **官网**：https://campusnet.journeymind.blog
- **问题反馈**：https://github.com/mi179/campusnet-guard/issues
