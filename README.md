# Avalon

### One Windows 10/11 x64 PC. Multiple independent desktops.

Avalon turns one Windows 10/11 x64 host into multiple independently accessible desktop instances. Each instance can have its own Windows session, virtual display, input, audio, applications, games, and Moonlight connection.

**One host. Multiple instances.**

## Languages

[English](README.md) · [简体中文](README-zh-CN.md) · [繁體中文](README-zh-TW.md) · [日本語](README-ja.md) · [한국어](README-ko.md) · [Español](README-es.md) · [Português (Brasil)](README-pt-BR.md) · [Deutsch](README-de.md) · [Français](README-fr.md) · [Italiano](README-it.md) · [Polski](README-pl.md) · [Русский](README-ru.md) · [Türkçe](README-tr.md) · [العربية](README-ar.md) · [हिन्दी](README-hi.md) · [Bahasa Indonesia](README-id.md) · [Tiếng Việt](README-vi.md) · [ไทย](README-th.md)

[Development log & feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / bug reports](https://github.com/AvalonStream/AvalonStream/issues)

---

## What is Avalon?

Avalon is a multi-session desktop streaming platform for Windows 10/11 x64. Instead of dedicating the whole PC to one interactive desktop, Avalon lets several independent Windows instances run side by side on the same host without requiring a full virtual machine for every user.

---

## Core capabilities

- Multiple independent Windows instances on one host
- A dedicated streaming context for every instance
- Per-instance virtual display, resolution and refresh rate
- Independent keyboard, mouse and session audio paths
- Session lifecycle managed by Avalon without keeping an external RDP client connected
- Web-based creation, pairing, status and diagnostics
- Moonlight remains the client experience on phones, tablets, TVs and PCs

---

## How it works

Create an instance, choose its display settings and pair a client. Avalon prepares the Windows session, virtual display, streaming context and lifecycle; then you connect with Moonlight.

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

## Designed for Moonlight

Avalon changes the host side rather than replacing the client you already know. Moonlight can continue to be used across Windows, Linux, macOS, Android, iOS/iPadOS, Android TV and other supported devices.

---

## Typical use cases

- Home gaming: different people use different instances at the same time
- Multi-account and multi-instance workloads
- Remote workstations on one high-performance PC
- Testing, automation and compatibility environments
- Homelab and self-hosted remote computing

---

## Isolation model

Avalon provides Windows session-level isolation, not full virtual-machine isolation. Instances have separate desktops, applications, displays, input paths and audio paths, while sharing the host Windows installation, kernel, CPU, GPU and physical hardware. Avalon should not be treated as a VM-grade security boundary.

---

## Platform and performance

Avalon targets 64-bit Windows 10 and Windows 11. Actual resolution, refresh rate, codec support, HDR behavior and the number of simultaneous instances depend on the GPU, drivers, encoder capabilities, network conditions and client hardware.

---

## Project status

Avalon is currently in Alpha. Interfaces, compatibility behavior and lower-level components are still evolving, so breaking changes and hardware-specific edge cases are expected.

---

## Development and feedback

This README is the stable product introduction. Real-time development notes and message guidance are maintained separately in the development log.

- [Development log & feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / bug reports](https://github.com/AvalonStream/AvalonStream/issues)

**One host. Multiple instances.**
