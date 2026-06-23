---
title: CampusNet Guard：把校园网重连做成普通人能用的小工具
date: 2026-06-10 10:00:00
updated: 2026-06-24 00:00:00
categories:
  - projects
tags:
  - campusnet
  - 校园网
  - 开源
  - python
  - Windows
  - Linux
---

校园网认证这件事本身不复杂，但它很烦。

宿舍电脑、实验室工位机、NAS、小主机、软路由，只要需要长期在线，就可能遇到断网、认证页不弹、设备数量限制、运营商选择错误、认证服务器地址不同这些问题。对懂网络的人来说还能排查，对普通用户来说就是一句话：又断了。

CampusNet Guard 想解决的是这个具体问题：**让用户自己的校园网账号，在断网时自动重新认证。**

## 它适合谁

- Windows 普通用户：下载 zip，解压，双击 GUI，添加账号，开始守护。
- Linux / NAS / 软路由用户：源码安装，用 `campusnet setup` 和 `campusnet start` 后台运行。
- 实验室或办公室工位：需要保持在线，但不想每次手动登录认证页。

它不适合这些用途：绕过认证、共享账号、突破在线数量限制、破解校园网策略。这些都不是这个项目要做的事。

## Windows 用户怎么用

1. 从 [GitHub Releases](https://github.com/mi179/campusnet-guard/releases/latest) 下载 `campusnet-guard-windows.zip`。
2. 解压后双击 `campusnet-guard-gui.exe`。
3. 打开“高级”页，添加账号，填写运营商、学号、密码和认证服务器地址。
4. 回到“主页”，点击“开始守护”。
5. 需要无感运行时，在“设置”页开启开机自启动。

不需要安装 Python，不需要打开命令行。

当前版本暂未代码签名，Windows SmartScreen 可能提示未知发布者。建议只从 GitHub Releases 或官网入口下载。

## Linux 用户怎么用

```bash
git clone https://github.com/mi179/campusnet-guard.git
cd campusnet-guard
bash scripts/linux/install.sh
source .venv/bin/activate
campusnet setup
campusnet start
```

Linux 版本主打 CLI Lite。图形界面不是当前重点，NAS、软路由、小主机更适合用 tmux、screen 或 systemd 长期运行。

## 我最在意的不是功能堆叠

这个项目真正难的地方不是多写几个按钮，而是把它做成普通人不会迷路的工具：

- 账号配置和程序文件分离，EXE 放哪里都不影响账号位置。
- 密码不明文保存，Windows 使用 DPAPI，Linux 使用本地密钥保护。
- 日常操作放主页，账号切换放高级页，减少普通用户误操作。
- 出问题时优先运行 `campusnet doctor`，给出下一步，而不是只抛异常。
- 开了代理、VPN、TUN 时不擅自改系统设置，只做检测和提示。

这也是后续重构的方向：不是“能跑就行”，而是让产品行为、文档、发布包、官网、博客都能互相对得上。

## 下载入口

- 官网：<https://campusnet.journeymind.blog>
- GitHub Releases：<https://github.com/mi179/campusnet-guard/releases/latest>
- 项目仓库：<https://github.com/mi179/campusnet-guard>

如果 GitHub 下载慢，可以先看官网里的国内备用下载说明。备用网盘可能失效，可信源仍以 GitHub Releases 为准。

## 免责声明

CampusNet Guard 只用于用户自己的校园网账号自动认证和断网重连，不绕过认证、不破解、不共享账号、不突破在线数量限制。学校或运营商的认证策略由网络系统决定，工具无法保证适配所有 Ruijie ePortal 环境。
