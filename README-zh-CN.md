# Avalon

### 一台 Windows 10/11 x64，多个彼此独立的桌面。

Avalon 把一台 Windows 10/11 x64 主机变成多个可以独立访问的桌面实例。每个实例都可以拥有自己的 Windows 会话、虚拟显示、输入、音频、应用、游戏以及 Moonlight 连接。

**一台主机，多个实例。**

[English](README.md)

[开发日志与留言说明](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / Bug 与功能建议](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon 是什么？

Avalon 是面向 Windows 10/11 x64 的多会话桌面串流平台。它不再让整台 PC 只能服务一个交互桌面，而是让多个独立 Windows 实例并行运行在同一台主机上，同时不需要为每个用户运行一整套完整虚拟机。

---

## 核心能力

- 一台主机并行运行多个独立 Windows 实例
- 每个实例拥有独立的串流上下文
- 每实例独立虚拟显示、分辨率与刷新率
- 独立键盘、鼠标与会话音频路径
- Avalon 自持会话生命周期，不需要外部 RDP 客户端持续连接
- 通过 Web 完成实例创建、配对、状态查看与诊断
- 手机、平板、电视与 PC 仍然使用熟悉的 Moonlight 客户端

---

## 它如何工作？

创建实例，选择显示设置并完成客户端配对。Avalon 会准备 Windows 会话、虚拟显示、串流上下文以及实例生命周期，之后直接通过 Moonlight 连接即可。

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## 为 Moonlight 而设计

Avalon 改变的是主机端，而不是要求用户更换熟悉的客户端。Moonlight 仍然可以用于 Windows、Linux、macOS、Android、iOS/iPadOS、Android TV 以及其他受支持设备。

---

## 典型使用场景

- 家庭游戏：不同用户同时进入不同实例
- 多账号、多开与多实例应用
- 把一台高性能 PC 作为多个远程工作站
- 测试、自动化与兼容性环境
- Homelab 与自托管远程计算

---

## 隔离模型

Avalon 提供的是 Windows 会话级隔离，而不是完整虚拟机隔离。实例拥有彼此独立的桌面、应用、显示、输入路径和音频路径，但仍共享主机 Windows 系统、内核、CPU、GPU 与物理硬件。因此 Avalon 不应被视为 VM 级安全边界。

---

## 平台与性能

Avalon 面向 64 位 Windows 10 与 Windows 11。实际分辨率、刷新率、编码格式、HDR 表现以及同时运行的实例数量，会受到 GPU、驱动、编码能力、网络环境和客户端硬件影响。

---

## 项目状态

Avalon 目前处于 Alpha 阶段。界面、兼容性行为以及底层组件仍在持续演进，因此可能出现破坏性变更和特定硬件上的边缘问题。

---

## 开发动态与反馈

这份 README 用于稳定的产品介绍。实时开发动态和留言说明单独维护在开发日志中。

- [开发日志与留言说明](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / Bug 与功能建议](https://github.com/AvalonStream/AvalonStream/issues)

**一台主机，多个实例。**
