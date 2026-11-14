# Avalon 1.1.0 — HDR and Controller Guide

This guide explains which HDR and controller features are available, how to enable them, and what to check when a feature does not work.

Windows requirements below refer to the **host running Avalon**. A controller normally connects to the **client running Moonlight**. Both sides, and the game itself, can affect which features reach the game.

- [Quick start](#quick-start)
- [HDR](#hdr)
- [Controllers](#controllers)
- [Multiple controllers and instances](#multiple-controllers-and-instances)
- [Troubleshooting](#troubleshooting)

## Quick start

| What you want to use | Start here |
| --- | --- |
| Ordinary controller buttons, sticks, and triggers | Connect the controller to your Moonlight client and leave Avalon's controller profile on **Auto**. |
| A game that expects an Xbox controller | Select **Xbox One** compatibility if the automatic profile is not accepted by the game. |
| A specific PlayStation controller profile | Select **DualShock 4**, **DualSense**, or **DualSense Edge** explicitly. |
| HDR streaming | Check **Environment Health → HDR**, then follow the [HDR setup steps](#enabling-hdr). |
| Independent Elite paddles or Series Share | Read the [Xbox extended-button requirements](#elite-paddles-and-series-share) first. |

Avalon 1.1.0 requires a supported x64 desktop edition of **Windows 10 2004, build 19041, or later**, including Windows 11. Windows 10 1903/1909, Windows Home, and Windows Server are outside this release's supported installation range.

Windows on ARM is not supported by this release.

Basic streaming and controller support have a broader Windows range than HDR or certain extended buttons. An unavailable optional feature does not mean ordinary SDR streaming or basic controller input is unavailable.

## HDR

### Windows support

These are the minimum **Windows OS builds accepted by Avalon's HDR controls**. Check the host's version with `winver`; the values are not driver-file version numbers.

| Host Windows version | HDR in Avalon 1.1.0 |
| --- | --- |
| Windows 10, including supported LTSC editions | SDR streaming is available. This release does not enable virtual-display HDR on Windows 10. |
| Windows 11 21H2, 22H2, or 23H2 | Outside the current HDR support range. Use SDR. |
| Windows 11 24H2 | Build **26100.8973** or later in the 26100 branch, subject to the compatibility check. |
| Windows 11 25H2 | Build **26200.8973** or later in the 26200 branch, subject to the compatibility check. |
| Windows 11 build 26300 branch | Build **26300.9550** or later, subject to the compatibility check. |
| Windows 11 build 28000 branch | Build **28000.2804** or later, subject to the compatibility check. |
| Other Windows builds | Not automatically treated as supported. Check Environment Health and the release notes for your Avalon version. |

**A version number alone is not enough.** Avalon also checks whether the installed system is compatible. A newer cumulative update within a listed branch can pass these checks automatically; an unfamiliar major branch does not inherit support merely because its build number is larger.

The table describes Avalon's current requirements. It does not identify the first Windows update that introduced any underlying HDR capability.

### What else is required?

For HDR on the viewing device, you also need:

- An HDR-capable display with HDR enabled on the client device.
- A Moonlight app and client device that support HDR playback.
- A compatible host graphics/encoding configuration capable of the required 10-bit HEVC or AV1 stream.
- An instance whose live display and encoding status actually reports HDR.

The host-side checks concern the instance's streamed virtual display. Enabling HDR on an unrelated host monitor does not confirm HDR in that instance.

Client-specific requirements differ. Consult the [Moonlight HDR setup guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#additional-requirements-for-hdr-streaming) for your client platform.

### Enabling HDR

1. Open **Environment Health** in Avalon's management panel and check the HDR entry.
2. Open the instance's display settings and set **HDR preference**:

   | Setting | Behavior |
   | --- | --- |
   | **Off** | Keep HDR disabled for this instance. |
   | **Auto — follow Moonlight** | Request HDR when the Moonlight client requests it and the configuration supports it. This is the recommended starting point. |
   | **Request HDR when available** | Ask for HDR when the system supports it. This cannot override an unsupported host, encoder, or client. |

3. Enable HDR in Moonlight's settings on a compatible client.
4. If Avalon says a **Windows restart is required**, save your work and restart the host normally. Reconnecting Moonlight or resuming from sleep does not replace that restart.
5. Start or reconnect to the instance as directed by the panel. Use **Check live encoding** to inspect the running stream.

**HDR preference**, **system readiness**, and **live HDR output** describe different things. Saving a preference, seeing a ready system, or selecting a 10-bit codec does not by itself confirm that the client is displaying HDR.

### Understanding HDR status

The wording may vary with the panel language, but the meanings are:

| Status | What it means / what to do |
| --- | --- |
| **Not supported** | The current Windows build or configuration is outside the supported range. SDR remains available. |
| **Off / not requested** | No instance currently requests the system preparation needed for HDR. Check the instance's preference if you intended to enable it. |
| **Preparing** | Avalon is processing the requested change. Refresh the status after it completes. |
| **Restart required** | The change needs a normal host restart before it can take effect. |
| **Ready** | System preparation is active. Check the running instance and client to confirm actual HDR output. |
| **Restoration requires a restart** | Turning HDR preparation off or restoring previous settings needs a normal host restart. |
| **Status unavailable / needs attention** | Avalon could not confirm readiness. Follow the panel's explanation; do not assume HDR is active. |

Avalon does not automatically restart Windows for these changes. If several instances request HDR, turning it off in one instance does not necessarily remove the shared system preparation still needed by another.

### SDR reference white

**SDR reference white** adjusts how bright SDR desktop and application content appears within HDR. It does not set the display's peak HDR brightness. This follows Windows' distinction between SDR white level and HDR display brightness; see [Microsoft's SDR white-level description](https://learn.microsoft.com/en-us/windows/win32/api/wingdi/ns-wingdi-displayconfig_sdr_white_level).

| Setting | Value |
| --- | --- |
| Default | **80 nits** |
| Allowed range | **80–480 nits**, whole numbers |

Start at 80. If SDR content looks too dim relative to HDR content, increase it gradually and compare the result on your client display. A higher value is not automatically more accurate. Use the display's normal brightness controls for an ordinary SDR stream.

Older configurations containing `0` still mean the default of 80 nits; the panel displays them as 80.

### After Windows updates

Avalon rechecks compatibility when its service starts and observes relevant system or configuration changes while it runs. Compatible updates within a supported branch can be handled without installing a new Avalon package for every update.

If a Windows update changes compatibility, the panel may show that HDR is unavailable or needs another restart. Keep using SDR while resolving it. Support for every future Windows release is not guaranteed.

## Controllers

### How controller selection works

Avalon forwards controller input reported by Moonlight and presents the selected controller profile to applications inside the instance. The physical controller's retail name is not always available to Avalon.

**Auto** selects a profile for each controller using the family and capabilities the client reports:

| Client-reported controller | Automatic profile |
| --- | --- |
| Xbox with independently reported rear paddles | Xbox Elite |
| Xbox with a Share button, without the paddle indication above | Xbox Series |
| Other Xbox controller | Xbox One |
| PlayStation-family controller | DualSense |
| Nintendo-family controller | Switch Pro-compatible |
| Generic, unknown, or Xbox 360-compatible source | Xbox One-compatible |

Automatic PlayStation-family information does not reliably distinguish DualShock 4, DualSense, and Edge. Select the exact output profile yourself when that distinction matters.

**Manual selection overrides Auto for the instance.** For example, choosing DualShock 4 presents connected controllers through that target profile, including an Xbox controller connected alongside a physical DS4. It does not add motion sensors, touch data, or extra buttons that the source/client never sends.

After changing a controller profile, save the setting, restart the instance, and reconnect Moonlight so the game sees the new device. Newly created instances use the new controller route; existing instances retain their saved input choices.

The table below describes the new default controller system in 1.1.0. A retained profile that explicitly selects an older input path keeps that selection.

### Controller support table

Basic controls means ordinary face buttons, directional pad, sticks, stick clicks, shoulder buttons, and triggers. Extra features require support from **the controller, Moonlight client, Windows, and the game**. Do not assume every firmware, connection method, or client platform exposes the same extras.

| Controller family | Basic controls | Extra features and boundaries |
| --- | --- | --- |
| **Xbox One** | Supported; analog triggers | Standard rumble feedback is supported through compatible clients and games. |
| **Xbox Wireless Controller — Series X\|S** | Supported; analog triggers | Rumble and conditional Share-button forwarding. Share is not available through every Windows input path or game. |
| **Xbox Elite / Elite Series 2 / Elite Series 2 Core** | Supported; analog triggers | Rumble and four independent paddles on compatible Windows 11 configurations. See the requirements below. Hardware profile/firmware management is not provided. |
| **DualShock 4 — PS4** | Supported; analog triggers | Motion, two-contact touchpad input, rumble, and light-bar feedback when the client and game support them. Select the DS4 profile explicitly when required. |
| **DualSense — PS5** | Supported; analog triggers | Motion, two-contact touchpad input, rumble, lighting, and adaptive-trigger effect forwarding when supported throughout the connection. Controller speakers/microphone passthrough and full audio-driven haptics are not included. |
| **DualSense Edge** | Supported; analog triggers | DualSense-profile features and two independent rear-button mappings. Select Edge explicitly. Remote Fn-button forwarding and on-controller profile management are not included. |
| **Switch Pro / client-normalized Joy-Con input** | Supported through a Switch Pro-compatible profile; digital ZL/ZR | Full Nintendo motion, HD Rumble, and controller-specific extras are not currently guaranteed. Separate Joy-Con pairing/combining is handled by the client, not Avalon. |
| **Switch 2 Pro / Joy-Con 2** | Compatibility-only if the client exposes a supported Nintendo or generic controller | No dedicated Switch 2 profile or promise of new features such as Joy-Con mouse mode. |
| **Xbox 360 and other generic controllers** | Xbox One-compatible output when the client supplies standard controls | The new route does not provide a dedicated native Xbox 360 target or every device-specific extension. |

Rumble, lighting, and trigger support describe effect forwarding. They do not promise identical strength, detail, or feel to a direct connection to the controller's original console.

Controller headset/audio passthrough, firmware updates, and hardware-profile management are outside this controller feature set. Battery reporting and other device-specific accessories are not guaranteed.

### Elite paddles and Series Share

An Elite paddle can behave in two different ways:

- **Mapped paddle:** the controller or client turns it into an ordinary button, such as A. Avalon receives A, and the game sees A. This uses the normal button path.
- **Independent paddle:** the client sends a separate rear-button input. All parts of the connection must preserve that extra control for the game to use it independently.

| Host Windows | Basic Xbox controls | Independent Elite paddles / extended Xbox buttons |
| --- | --- | --- |
| Supported Windows 10 versions | Available | Independent paddles are not an officially supported feature of Avalon's Windows 10 controller route. Share availability also varies. |
| Windows 11 21H2 / 22H2 / 23H2 | Available | No general independent-paddle or Share guarantee. |
| Updated Windows 11 24H2 / 25H2 and compatible newer configurations | Available | Conditionally available when the client reports the controls and Windows/the application expose them. |

There is no single Windows build number that guarantees these buttons in every setup. Keep basic input, extended buttons, and HDR requirements separate: passing the HDR version check does not certify paddle support, and paddle support does not enable HDR.

This does **not** mean Elite controllers are unusable on Windows 10. Their ordinary controls and paddles mapped to ordinary buttons remain usable. It also does not impose the same Xbox-specific restriction on PlayStation rear buttons, motion, or touchpad input.

For model names: **Xbox Wireless Controller for Series X\|S** is the standard controller family. **Elite Series 2** and **Series 2 Core** belong to the Elite family; “Series 2” is not another name for the standard Series X\|S controller.

## Multiple controllers and instances

Controllers are routed to the instance receiving their client's input. Stopping one instance should not disconnect controllers belonging to another instance.

[XInput games expose up to four controller slots](https://learn.microsoft.com/en-us/windows/win32/xinput/getting-started-with-xinput#multiple-controllers). This is an application input-interface limit, not a separate Avalon-wide pool of four controllers shared by every isolated instance. The number recognized by a particular game still depends on its input support and the client/platform limits.

Multiple clients connected to **one** instance share that instance's desktop and applications. They do not receive separate Windows sessions. The instance's streaming-channel setting limits simultaneous clients. Your license limits instance usage, while host resources and the game's local-multiplayer support provide additional limits.

If you open several Moonlight windows on the same client, they may each forward the same physical controller. That can make it control several streams at once even though the host's instances remain isolated. Enable input forwarding only for the windows you intend to control.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| HDR settings are unavailable | Check the **host** OS build and Environment Health. An HDR-capable viewing display alone does not make the host compatible. |
| HDR is ready but the picture is SDR | Enable HDR in the client, reconnect as directed, and inspect the instance's **live encoding** status. A saved preference or a 10-bit codec is not sufficient by itself. |
| The panel still requests a restart | Restart the host normally. Reconnecting, restarting just the instance, or resuming from sleep may leave a system change unapplied. |
| HDR looks dim or washed out | Confirm HDR is active at both ends before adjusting brightness. Check client/display calibration and SDR reference white. |
| No controller input arrives | Confirm the controller works locally on the client and that Moonlight controller input is enabled. Reconnect after adding or changing devices if the client does not detect them. |
| Buttons work, but paddles/motion/touch do not | Check the feature table, selected profile, and what the client actually forwards. A standard-button remap is not an independent extra button. |
| A PlayStation controller appears as Xbox | Check the selected Avalon profile and any client/game remapping. For an Xbox-only game, Xbox One compatibility may be the appropriate profile. |
| Nintendo A/B or X/Y feels swapped | Check the target profile and the client's button-swap settings. Button names and physical positions differ between controller families. |
| Input stops when Moonlight is in the background | Enable the client's background-controller-input option where available. Client input options vary by platform; see the [Moonlight setup guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#keyboardmousegamepad-input-options). |
| Guide, Home, or Share is not seen by the game | The client or Windows may handle these buttons outside the game. Their behavior is separate from ordinary game buttons. |

For a support report, include the Avalon version, host Windows build from `winver`, client platform/Moonlight version, controller model and connection method, chosen profile, and the affected feature. Include the relevant Environment Health or instance status. **Do not attach activation files, passwords, or pairing PINs.**

Last reviewed for Avalon 1.1.0: **2026-11-14**.
