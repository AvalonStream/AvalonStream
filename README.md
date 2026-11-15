<!-- avalon-readme-revision: 2026-11-15.1 -->

<div align="center">

# Avalon

### One Windows PC. Multiple independent desktops.

Run separate Windows desktop instances on one host, each with its own display, input, audio playback, applications, and Moonlight connection.

**Avalon 1.1.0 is available.**

[Download for Windows x64](https://github.com/AvalonStream/AvalonStream/releases/download/v1.1.0/Avalon-Setup-1.1.0.exe) · [Release notes](https://github.com/AvalonStream/AvalonStream/releases/tag/v1.1.0) · [HDR and controller guide](HDR-Controller-README.md) · [Website](https://avalons.cc/)

**One host. Multiple instances.**

</div>

## What is Avalon?

Avalon is a multi-session desktop streaming platform for Windows 10/11 x64. It lets several users connect to separate desktops on the same PC without running a full virtual machine for each user.

```text
                Windows 10/11 x64 Host
                         │
                      Avalon
                         │
           ┌─────────────┼─────────────┐
           │             │             │
      Instance 01    Instance 02    Instance 03
           │             │             │
       Moonlight      Moonlight      Moonlight
          TV            Tablet         Laptop
```

Each instance has a separate Windows session and streaming connection. One person can play on a TV while another uses a tablet or laptop for a different game or application.

Instances share the host's Windows installation, kernel, CPU, GPU, memory, and storage. Avalon provides **session-level isolation**, not a VM-grade security boundary.

## Features

| Feature | What you can do |
| --- | --- |
| **Independent desktops and streams** | Run separate applications, games, and audio playback in each Windows session. |
| **Virtual displays** | Set resolution and refresh rate per instance without a physical monitor for every desktop. |
| **Keyboard and mouse** | Use the new RDS input backend for session-specific input, including supported UAC interactions. The existing SendInput option remains available. |
| **Controllers** | Use Xbox, PlayStation, and Nintendo Switch-family controllers with automatic or manual profile selection. Advanced features depend on the controller, client, Windows, and game. |
| **Optional HDR** | Configure HDR per instance, view readiness in Environment Health, and check the running stream's encoding status. |
| **Touch and pen input** | Forward native screen touch and stylus events from compatible Moonlight clients. Device and application support vary. |
| **Flexible instance creation** | Use quick or custom creation, multilingual names, new local accounts, existing accounts, and generated strong passwords. |
| **Session management** | Start, stop, and recover instances centrally, including restoration of previously running instances after a host restart. No external RDP client needs to stay connected. |
| **Installation and updates** | Install, uninstall, and perform configuration-preserving reinstalls or updates using the native setup and recovery system. |
| **Web management** | Manage pairing, display/input settings, activation, environment health, and diagnostics in one panel. |

Version 1.1.0 also improves pairing, remote text rendering, application compatibility, update recovery, activation compatibility, and log retention. See the [release notes](https://github.com/AvalonStream/AvalonStream/releases/tag/v1.1.0) for the changes since 1.0.2.

## Requirements

These requirements apply to the **PC running Avalon**. The Moonlight client can use a different operating system.

| Item | Requirement |
| --- | --- |
| **Host Windows** | A supported x64 desktop edition of **Windows 10 2004 (build 19041) or later**, including Windows 11. |
| **Outside the installation support range** | Windows 10 1903/1909, Windows Home, Windows Server, 32-bit Windows, and Windows on ARM. |
| **Permissions** | Administrator permission for installation, removal, and maintenance. |
| **Graphics and resources** | Compatible graphics hardware/drivers and sufficient CPU, RAM, and encoding capacity for the streams you want to run. |
| **Client** | A compatible Moonlight app and a network connection suitable for the requested resolution and frame rate. |

Moonlight clients are available for Windows, Linux, macOS, Android, iOS/iPadOS, and compatible TV/streaming devices. Features differ between platforms and client versions.

**HDR and advanced controller features have additional requirements.** Check the [HDR and controller support guide](HDR-Controller-README.md) for Windows versions, controller models, Elite paddles, Series Share, PlayStation extensions, and touch/pen limitations.

The installer includes test-signed drivers, not WHQL-certified drivers. Windows security policies can affect installation and loading.

## Get started

1. [Download Avalon 1.1.0](https://github.com/AvalonStream/AvalonStream/releases/download/v1.1.0/Avalon-Setup-1.1.0.exe) and install it from a normal logged-in Windows desktop with administrator permission.
2. Open the host's management panel at **[https://localhost:48080](https://localhost:48080)** and complete the initial setup. It uses a local HTTPS certificate; verify the device/address before proceeding through a certificate warning.
3. Create an instance using quick or custom creation, then **start it**. Creating an instance does not automatically start it.
4. Add the instance's host address and streaming port, as shown by Avalon, to Moonlight. Enter Moonlight's pairing PIN in that instance's pairing page in Avalon.
5. Connect to Desktop or a configured application. Complete any Windows first-user setup if prompted.

Use the instance's streaming port for Moonlight; port **48080** is the management panel. Configure HDR and controller profiles using the [support guide](HDR-Controller-README.md).

## Upgrading and reinstalling

Back up your configuration and **license.dat** before maintenance.

| Installed version | How to proceed |
| --- | --- |
| **1.0.2 or earlier** | Uninstall the old version before installing 1.1.0. In-place updating from these versions is not supported. |
| **1.1.0 baseline or later** | Run an installer for the same or a newer version and choose reinstall/update. The maintenance workflow preserves configuration and provides rollback/recovery if the operation fails. |

Maintenance may stop instances and disconnect remote sessions. Save work inside those instances first. Follow any restart or pending-recovery instructions in the installer; do not manually delete recovery files while an operation is incomplete.

When removing instances or uninstalling, review the retain/discard choices. Accounts created by Avalon remain eligible for cleanup, including after reuse. Borrowed existing Windows accounts and the built-in Administrator account are protected from account cleanup.

## Free use and activation

| Mode | Limits |
| --- | --- |
| **Without activation** | One created instance, one running instance, and up to **60 FPS**. |
| **Activated** | The limits granted by your license apply. The product-wide instance cap is **330**; practical concurrency depends on hardware, applications, and stream settings. |

Purchase from **More → Buy license** in the panel. Activation is device-bound; hardware identity changes may require support.

Keep a backup of **license.dat**. A valid perpetual activation can be verified offline and restored on the same eligible device after reinstalling Windows. Time-limited activation requires online time verification and expires on its stated date.

Activation does not guarantee a particular resolution, frame rate, HDR mode, or number of simultaneous streams. Windows, application, game, and account licensing requirements still apply.

## Compatibility notes

- **HDR and controller extras:** availability depends on the host, client, device, and application. The support guide separates basic input from optional extensions.
- **Mobile keyboards:** soft-keyboard text can fail at Windows UAC prompts in 1.1.0. General UAC mouse/keyboard support does not guarantee every mobile text-input method.
- **Audio:** instances have independent playback. Client microphone passthrough is not included.
- **Games and applications:** DRM, anti-cheat, account restrictions, and multi-session behavior vary; not every application supports simultaneous sessions.
- **System updates:** Windows and graphics-driver updates can change compatibility. Check Environment Health and follow any restart or recovery guidance.
- **Performance:** GPU/encoder capacity, resolution, refresh rate, codec, network quality, client decoding, and simultaneous instances all affect the result.

## Support and feedback

- [HDR, controllers, and other client inputs](HDR-Controller-README.md)
- [Downloads and previous versions](https://github.com/AvalonStream/AvalonStream/releases)
- [Report a reproducible bug](https://github.com/AvalonStream/AvalonStream/issues)
- [Questions and ideas](https://github.com/AvalonStream/AvalonStream/discussions)
- [Avalon website](https://avalons.cc/)

For a bug report, include your Avalon version, host Windows build, GPU/driver, client name/version, reproduction steps, and relevant diagnostics. Review logs before sharing them; do not post passwords, activation files, pairing PINs, or purchase links containing private tokens.

---

<div align="center">

**One host. Multiple instances.**

</div>
