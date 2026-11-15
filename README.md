<!-- avalon-readme-revision: 2026-11-15.2 -->

<div align="center">

# Avalon

### One Windows 10/11 x64 PC. Multiple independent desktops.

Turn a single Windows 10/11 x64 machine into multiple independently accessible desktop instances, each with its own display, input, audio, applications, and remote streaming connection.

**One host. Multiple instances.**

</div>

---

## What is Avalon?

Avalon is a multi-session desktop streaming platform for Windows 10/11 x64.

Instead of letting one PC serve only one interactive desktop at a time, Avalon allows the same machine to host multiple independent Windows instances simultaneously.

Each instance can have its own:

- Windows desktop session
- Virtual display
- Resolution and refresh rate
- Input stream
- Audio stream
- Applications and games
- Remote Moonlight connection

This makes it possible for one powerful PC to behave more like several remotely accessible computers, without requiring a full virtual machine for every user.

---

## What does this look like?

Imagine one Windows 10/11 x64 PC running three Avalon instances:

```text
                Windows 10/11 x64 Host
                       │
                ┌──────┴──────┐
                │    Avalon    │
                └──────┬──────┘
                       │
         ┌─────────────┼─────────────┐
         │             │             │
         ▼             ▼             ▼
    Instance 01    Instance 02    Instance 03
         │             │             │
         ▼             ▼             ▼
     Moonlight      Moonlight      Moonlight
        TV            Tablet         Laptop
```

Each client connects to its own Windows desktop.

The instances run side by side without sharing the same desktop, mouse cursor, audio output, or application session.

---

## Why Avalon?

Traditional remote desktop tools are usually designed around one user controlling one desktop.

Virtual machines solve isolation well, but they also add additional operating systems, memory overhead, storage usage, GPU complexity, and management cost.

Avalon takes a different approach.

It builds on Windows sessions, virtual displays, independent streaming processes, and centralized lifecycle management so that multiple interactive desktops can coexist on one Windows 10/11 x64 host.

The complexity stays inside Avalon.

For the user, the workflow is simple:

```text
Create an instance
        ↓
Configure display and pairing
        ↓
Open Moonlight
        ↓
Connect
```

---

## Core capabilities

### Multiple independent instances

Run multiple Windows desktop sessions on the same host at the same time.

Each instance behaves as its own interactive desktop environment.

### Independent streaming

Every instance has its own streaming context and can be connected to independently using a Moonlight client.

A television can connect to one instance while a tablet or another computer connects to another.

### Independent display

Each instance can use its own virtual display configuration, including resolution and refresh rate.

Display handling is managed by Avalon rather than requiring a physical monitor for every instance.

Optional HDR is available on compatible Windows 11 configurations. See the [HDR and controller guide](HDR-Controller-README.md) for requirements and setup.

### Independent input

Keyboard and mouse input are routed to the intended Windows session instead of being shared across instances.

Avalon 1.1.0 adds an RDS keyboard and mouse backend alongside the existing SendInput option, plus Xbox, PlayStation, and Nintendo Switch-family controller support with automatic or manual profile selection.

Compatible Moonlight clients can also forward native screen touch and pen input. Advanced controller and pen/touch features depend on the client, device, Windows version, and application; see the [support guide](HDR-Controller-README.md).

### Independent audio

Each instance uses its own Windows session audio path so users can listen to different applications or games without mixing audio between instances.

### Session lifecycle management

Avalon creates and maintains sessions itself.

A separate external RDP client does not need to remain connected just to keep an instance alive.

Previously running instances can be restored after a Windows restart.

### Web management

Instances are managed from one web interface.

Typical operations include:

- Create and remove instances
- Start and stop instances
- Configure resolution and refresh rate
- Configure controller profiles and HDR preferences
- Pair Moonlight clients
- Inspect connection status
- Check environment health
- View diagnostics
- Manage host-level settings

No command-line workflow is required for normal day-to-day use.

---

## Designed for Moonlight

Avalon is built around the familiar Moonlight streaming experience.

You can continue using Moonlight on devices such as:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Smart TVs and streaming devices supported by Moonlight

Avalon changes how the host is organized.

It does not require users to learn a completely new streaming client.

---

## Use cases

### Home gaming

Turn one gaming PC into multiple independent gaming environments for different people in the same household.

One person can play from the living room while another connects from a handheld or laptop.

### Multi-account and multi-instance workloads

Run different applications, accounts, or game sessions in separate Windows environments on the same machine.

### Remote workstation access

Use one powerful desktop as several independently accessible remote workspaces.

### Testing and development

Maintain multiple Windows sessions for software testing, automation, compatibility work, or isolated user environments.

### Homelab and self-hosting

Use a high-performance Windows machine as a centrally managed multi-user remote computing host.

---

## How Avalon works

Avalon internally coordinates several layers of the system:

```text
Web Management
      │
      ▼
Avalon Control Service
      │
      ▼
Windows Sessions
Virtual Displays
Streaming Processes
Input / Audio Routing
      │
      ▼
Moonlight Clients
```

The implementation underneath this model is intentionally hidden from normal users.

You create an instance.

Avalon prepares the session, display, streaming environment, and lifecycle.

Then you connect.

---

## Isolation model

Avalon provides **Windows session-level isolation**.

Each instance has its own interactive Windows session, desktop, applications, display, input path, and audio path.

However, Avalon instances are **not full virtual machines**.

They still share:

- The same Windows host installation
- The same kernel
- The same physical CPU
- The same physical GPU
- The same host hardware resources

Avalon should therefore not be treated as a VM-grade security boundary.

Its goal is efficient multi-user and multi-desktop streaming, not hardware-level virtualization.

---

## Current status

**Avalon 1.1.0 is now available.**

[Download Avalon for Windows x64](https://github.com/AvalonStream/AvalonStream/releases/download/v1.1.0/Avalon-Setup-1.1.0.exe) · [Release notes and previous versions](https://github.com/AvalonStream/AvalonStream/releases)

- Supported hosts: Windows 10 x64 version 2004 (build 19041) or later, and Windows 11 x64. Windows Home editions, Windows Server, 32-bit Windows, and Windows on ARM are not supported.
- The installer includes the host application, web management, session provider, virtual display, and input components. Administrator permission is required for installation and removal.
- Create an instance, start it from the management panel, and pair your Moonlight client. Creating an instance does not automatically start it.
- Without activation, Avalon supports one created instance, one running instance, and up to 60 FPS. Paid activation applies the limits granted by your license; the system-wide limit remains 330 instances, and practical concurrency depends on your hardware.
- Purchase from **More → Buy license** in the Avalon panel. Keep the delivered **license.dat** file: it can restore a perpetual license on the same licensed device after reinstalling Windows, including while offline. Changes to the motherboard or system drive can affect device-bound activation.

When upgrading from 1.0.2 or earlier, back up your configuration and **license.dat**, uninstall the old version, then install 1.1.0. From the 1.1.0 baseline onward, installers for the same or a newer version support configuration-preserving reinstalls/updates with rollback and recovery if the operation fails.

The 1.1.0 package includes test-signed drivers, not WHQL-certified drivers. Windows security policies can affect installation and loading.

HDR and advanced controller support have additional requirements described in the [support guide](HDR-Controller-README.md). Mobile soft-keyboard text can fail at Windows UAC prompts in 1.1.0; native pen/touch support does not remove this limitation. Client microphone passthrough is not included.

Hardware, encoder, game, anti-cheat, and network compatibility still vary. Intermittent audio issues on some cross-network IPv6 connections remain under investigation. Please report reproducible issues with the Windows version, GPU, client, and relevant logs; do not include passwords, license files, or purchase links containing private tokens.

---

## Platform

Current target:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon is designed specifically around the Windows desktop and session model.

Support for other host operating systems is not currently a project goal.

---

## Performance

Actual streaming performance depends on many factors, including:

- GPU
- Encoder support
- Graphics driver
- Resolution
- Refresh rate
- Codec
- Network quality
- Client decoding capability
- Number of simultaneous instances

Avalon does not guarantee a specific resolution, refresh rate, HDR mode, or number of concurrent instances on every system.

HDR and controller compatibility requirements are documented in the [HDR and controller guide](HDR-Controller-README.md).

---

## Project philosophy

Avalon is built around a simple idea:

> A powerful PC should not be limited to one screen, one desktop, and one user at a time.

The host may be one machine.

The experiences running on it do not have to be.

---

## Development

Future versions of Avalon are still in development. Stay tuned for a more reliable product, better performance, and support for more features!

Report reproducible bugs through [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues). Use [GitHub Discussions](https://github.com/AvalonStream/AvalonStream/discussions) for questions, ideas, and community feedback.

---

<div align="center">

### Avalon

**One host. Multiple instances.**

</div>
