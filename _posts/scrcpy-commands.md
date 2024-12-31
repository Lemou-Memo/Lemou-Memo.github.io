---
title: Scrcpy 安装和使用指南
date: 2024-12-31 14:30:00 +0800
categories: [工具教程]
tags: [设备投屏到电脑]
---


# Scrcpy 安装和使用指南

## 安装说明

### Windows 安装方法

1. 使用 winget 安装（推荐）
```bash
# 安装 scrcpy
winget install --exact Genymobile.scrcpy
```

注意：使用 winget 前请确保系统支持：
- Windows 11：预装 winget
- Windows 10：需要安装 App Installer
  - 方法1：从 Microsoft Store 安装 App Installer
  - 方法2：访问 https://github.com/microsoft/winget-cli/releases 下载

检查 winget 是否可用：
```bash
winget --version
```

### 备选安装方法

```bash
# 使用 Chocolatey
choco install scrcpy

# 使用 Scoop
scoop install scrcpy
```

也可以直接从 GitHub 下载发布版本：
https://github.com/Genymobile/scrcpy/releases

## 基础连接

```bash
# 基本启动
scrcpy

# 指定设备（多设备时）
scrcpy --serial=DEVICE_ID

# 使用TCP/IP连接
scrcpy --tcpip=192.168.1.100:5555

# 设置端口
scrcpy --port=27184
```

## 显示设置

```bash
# 设置分辨率（限制宽度为1024px）
scrcpy --max-size=1024

# 设置帧率
scrcpy --max-fps=30

# 全屏显示
scrcpy --fullscreen

# 窗口置顶
scrcpy --always-on-top

# 设置窗口标题
scrcpy --window-title="My Phone"

# 旋转屏幕（0:不旋转, 1:90度, 2:180度, 3:270度）
scrcpy --rotation=1
```

## 录制功能

```bash
# 录制（支持格式：mp4/mkv）
scrcpy --record=file.mkv

# 仅录制，不显示镜像
scrcpy --no-display --record=file.mkv

# 录制时显示触摸点
scrcpy --record=file.mkv --show-touches

# 录制时指定视频码率
scrcpy --record=file.mkv --video-bit-rate=8M

# 不录制音频
scrcpy --no-audio --record=file.mkv
```

## 性能和画质

```bash
# 设置视频码率
scrcpy --video-bit-rate=2M

# 使用特定编码器
scrcpy --encoder=h264

# 设置画质（0-100）
scrcpy --display-buffer=50

# 关闭设备屏幕（省电）
scrcpy --turn-screen-off
```

## 输入控制

```bash
# 显示触摸点
scrcpy --show-touches

# 禁用电脑键盘输入
scrcpy --no-key-repeat

# 禁止电脑控制设备
scrcpy --no-control

# 禁用鼠标右键返回
scrcpy --no-key-repeat

# 关闭剪贴板同步
scrcpy --no-clipboard-autosync
```

## 其他实用选项

```bash
# 保持设备常亮
scrcpy --stay-awake

# 禁用设备屏保
scrcpy --disable-screensaver

# 渲染过期帧
scrcpy --render-expired-frames

# 关闭电源时自动断开
scrcpy --power-off-on-close
```

## 常用组合命令

```bash
# 高质量录制
scrcpy --max-size=1024 --max-fps=30 --video-bit-rate=8M --record=file.mkv

# 低延迟观看
scrcpy --max-size=800 --video-bit-rate=2M --render-expired-frames

# 省电模式录制
scrcpy --turn-screen-off --stay-awake --video-bit-rate=2M --record=file.mkv

# 远程控制最佳实践
scrcpy --max-size=800 --video-bit-rate=2M --show-touches --stay-awake
```

## 帮助命令

```bash
# 显示帮助信息
scrcpy --help

# 显示版本信息
scrcpy --version
```
