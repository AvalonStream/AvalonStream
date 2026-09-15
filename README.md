<div align="center">

# Avalon

### One Windows 11 PC. Multiple independent desktops.

Turn a single Windows 11 machine into multiple independently accessible desktop instances, each with its own display, input, audio, applications, and remote streaming connection.

**One host. Multiple instances.**

[简体中文](README-zh-CN.md)

</div>

---

## What is Avalon?

Avalon is a multi-session desktop streaming platform for Windows 11.

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

Imagine one Windows 11 PC running three Avalon instances:

```text
                Windows 11 Host
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

It builds on Windows sessions, virtual displays, independent streaming processes, and centralized lifecycle management so that multiple interactive desktops can coexist on one Windows 11 host.

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

### Independent input

Keyboard and mouse input are routed to the intended Windows session instead of being shared across instances.

Avalon is also designed around per-instance device isolation as the input stack continues to evolve.

### Independent audio

Each instance uses its own Windows session audio path so users can listen to different applications or games without mixing audio between instances.

### Session lifecycle management

Avalon creates and maintains sessions itself.

A separate external RDP client does not need to remain connected just to keep an instance alive.

### Web management

Instances are managed from one web interface.

Typical operations include:

- Create and remove instances
- Start and stop instances
- Configure resolution and refresh rate
- Pair Moonlight clients
- Inspect connection status
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

Avalon is currently in **Alpha**.

The architecture, management interface, compatibility layer, and device stack are still evolving.

Expect:

- Breaking changes
- Incomplete hardware compatibility
- UI changes
- Driver and session edge cases
- Features that may change before stable release

Avalon is not yet intended to be treated as production-critical infrastructure.

Testing, feedback, logs, and reproducible bug reports are extremely valuable during this stage.

---

## Platform

Current target:

```text
Windows 11
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

Compatibility documentation will become more detailed as testing expands.

---

## Project philosophy

Avalon is built around a simple idea:

> A powerful PC should not be limited to one screen, one desktop, and one user at a time.

The host may be one machine.

The experiences running on it do not have to be.

---

## Development

Avalon is under active development.

The latest development information, known issues, compatibility notes, and technical details are maintained in this repository.

For bug reports and feature requests, use the repository issue tracker.

---

## License

License information will be provided as the project approaches public release.

---

<div align="center">

### Avalon

**One host. Multiple instances.**

</div>
