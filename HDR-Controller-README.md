# Avalon 1.1.0 — HDR and Controller Support

Avalon runs on the **host PC**. Moonlight runs on the **client device**, where you normally connect your controllers, touchscreen, or pen.

**Host requirements:** a supported x64 desktop edition of **Windows 10 2004 (build 19041) or later**, including Windows 11. Windows Home, Windows Server, Windows on ARM, and Windows 10 1903/1909 are outside this release's installation support.

- [HDR: requirements and setup](#1-hdr)
- [Controllers: models, features, and setup](#2-controllers)
- [Appendix: Moonlight touch, pen, and mobile keyboard](#appendix-moonlight-touch-pen-and-mobile-keyboard)

## 1. HDR

### Windows support

These requirements apply to the **Avalon host**, not the device displaying the stream. Check the host with `winver`.

| Host Windows version | HDR support in Avalon 1.1.0 |
| --- | --- |
| Windows 10, including supported LTSC editions | SDR available; virtual-display HDR is not enabled in this release. |
| Windows 11 21H2 / 22H2 / 23H2 | Use SDR; outside the current HDR support range. |
| Windows 11 24H2 | **26100.8973 or later**, within the 26100 branch and subject to compatibility checks. |
| Windows 11 25H2 | **26200.8973 or later**, within the 26200 branch and subject to compatibility checks. |
| Windows 11 build 26300 branch | **26300.9550 or later**, subject to compatibility checks. |
| Windows 11 build 28000 branch | **28000.2804 or later**, subject to compatibility checks. |
| Other Windows builds | Check Environment Health and Avalon's release notes; support is not assumed. |

Avalon checks the installed system as well as its version. Compatible updates within a listed branch can pass automatically; an unfamiliar major branch does not inherit support from a larger build number. An unavailable HDR option leaves SDR streaming available.

### Enable HDR

You need an **HDR-capable client display**, HDR playback support in your Moonlight client, and a host encoding configuration that supports **10-bit HEVC or AV1**. Client requirements vary; see [Moonlight's HDR setup guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#additional-requirements-for-hdr-streaming).

1. Check **Environment Health → HDR** in Avalon's panel.
2. In the instance's display settings, select **Auto — follow Moonlight** for HDR preference. **Off** disables HDR for that instance; **Request HDR when available** requests it without overriding compatibility requirements.
3. Enable HDR in Moonlight and on the viewing device. If Avalon requests a **host restart**, save your work and restart Windows normally.
4. Start or reconnect to the instance as directed, then use **Check live encoding** to confirm the running stream's HDR status.

A saved preference or a **Ready** system status alone does not confirm HDR playback. Reconnecting Moonlight or resuming from sleep does not apply a change that requires a Windows restart.

### Status and brightness

| Panel status | Meaning / action |
| --- | --- |
| **Not supported** | Use SDR on the current Windows build or configuration. |
| **Off / not requested** | Check the instance's HDR preference if you intended to enable HDR. |
| **Preparing** | Wait for preparation to finish, then refresh the status. |
| **Restart required** | Restart the host normally; this also applies when restoring previous system settings. |
| **Ready** | System preparation is active; check the instance's live stream and client HDR settings. |
| **Unavailable / needs attention** | Follow the explanation in the panel; HDR readiness could not be confirmed. |

**SDR reference white:** default **80 nits**, adjustable from **80 to 480 nits** in whole numbers. It controls SDR desktop/application brightness within HDR, not the display's peak HDR brightness. Start at 80 and increase gradually if SDR content looks too dim. See [Microsoft's SDR white-level explanation](https://learn.microsoft.com/en-us/windows/win32/api/wingdi/ns-wingdi-displayconfig_sdr_white_level).

If HDR looks washed out or unexpectedly dim, confirm HDR is active on both ends before adjusting brightness. If several instances request HDR, disabling it in one instance may leave shared system preparation active for the others.

After Windows updates, Avalon rechecks compatibility. Follow any new restart or compatibility notice in Environment Health; support for every future update is not guaranteed.

## 2. Controllers

### Controller support

**Basic controls** means face buttons, directional pad, sticks, stick clicks, shoulder buttons, and triggers. Extra features require support from **the controller, Moonlight client, host Windows, and game**; USB/Bluetooth behavior can differ.

| Controller family | Basic controls | Extras and limitations |
| --- | --- | --- |
| **Xbox One** | Supported; analog triggers | Standard rumble through compatible clients and games. |
| **Xbox Wireless Controller — Series X\|S** | Supported; analog triggers | Rumble; Share forwarding depends on Windows, the client, and application. |
| **Xbox Elite / Elite Series 2 / Elite Series 2 Core** | Supported; analog triggers | Rumble; four independent paddles on compatible Windows 11 configurations. See [extended-button requirements](#elite-paddles-and-series-share). |
| **DualShock 4 — PS4** | Supported; analog triggers | Motion, two-contact touchpad input, rumble, and light-bar feedback. Choose the DS4 profile when needed. |
| **DualSense — PS5** | Supported; analog triggers | Motion, two-contact touchpad input, rumble, lighting, and adaptive-trigger effects. No speaker/microphone passthrough or full audio-driven haptics. |
| **DualSense Edge** | Supported; analog triggers | DualSense-profile features plus two independent rear-button mappings. Choose Edge explicitly. Remote Fn forwarding and hardware-profile management are not included. |
| **Switch Pro / client-normalized Joy-Con input** | Switch Pro-compatible input; digital ZL/ZR | Motion, HD Rumble, and Nintendo-specific extras are not guaranteed. The client handles Joy-Con pairing/combining. |
| **Switch 2 Pro / Joy-Con 2** | Compatibility-only when the client exposes a supported Nintendo or generic controller | No dedicated Switch 2 profile or guarantee of features such as Joy-Con mouse mode. |
| **Xbox 360 / other generic controllers** | Xbox One-compatible output when the client supplies standard controls | No dedicated native Xbox 360 target or guarantee of device-specific extras on the new route. |

Effect forwarding does not guarantee the same rumble or trigger feel as a direct console connection. Controller audio/headset passthrough, firmware updates, and hardware-profile management are not included. Battery reporting and accessory support depend on the device and client.

### Choose a profile

Start with **Auto**. It chooses separately for each controller using information reported by Moonlight:

| Client-reported input | Auto selects |
| --- | --- |
| Xbox with independent paddles | Xbox Elite |
| Xbox with Share, without the paddle indication above | Xbox Series |
| Other Xbox or generic controller | Xbox One-compatible |
| PlayStation family | DualSense |
| Nintendo family | Switch Pro-compatible |

Choose **DualShock 4**, **DualSense**, or **DualSense Edge** explicitly when the exact PlayStation profile matters. For a game that accepts only Xbox-style input, try **Xbox One** compatibility.

**A manual profile applies to the whole instance.** For example, selecting DS4 also presents an Xbox controller connected alongside a physical DS4 through the DS4 target profile. It cannot add sensor data or buttons that the client does not send.

After changing the profile, save, restart the instance, and reconnect Moonlight. New instances use the new controller route; existing instances retain their saved input choices. The support table above describes the new route.

### Elite paddles and Series Share

**Elite Series 2 / Series 2 Core** belong to the Elite family; they are distinct from the standard Series X\|S controller.

A paddle mapped to **A**, for example, reaches the game as A through the normal button path. An **independent paddle** reaches the game as an additional control and requires extra support throughout the connection.

| Host Windows | Basic Xbox controls / paddles mapped to ordinary buttons | Independent Elite paddles / Series Share |
| --- | --- | --- |
| Supported Windows 10 versions | Available | Independent paddles are not an officially supported Avalon feature on Windows 10. Share availability varies. |
| Windows 11 21H2 / 22H2 / 23H2 | Available | No general independent-paddle or Share guarantee. |
| Updated Windows 11 24H2 / 25H2 and compatible newer configurations | Available | Conditional on the client reporting the controls and Windows/the application exposing them. |

There is **no universal Windows build number** that guarantees these extras. HDR eligibility does not certify paddle support. This Xbox-specific boundary does not impose the same restriction on PlayStation rear buttons, motion, or touchpad input.

### Multiple controllers and clients

- Each client's input is routed to its receiving instance. Instances have separate controller routing; stopping one should not disconnect another's devices.
- [XInput exposes four controller slots to applications](https://learn.microsoft.com/en-us/windows/win32/xinput/getting-started-with-xinput#multiple-controllers). This is not an Avalon-wide pool of four controllers. Actual controller counts depend on the client, game, and input interface.
- Multiple clients joining **one instance** share its desktop and applications. The instance's streaming-channel setting limits simultaneous clients; resources and license limits also apply.
- Multiple Moonlight windows on one client can each forward the same physical controller. Check each window's input settings if it controls more than one stream.

### If a controller feature is missing

First check that it works locally on the client, then check the selected Avalon profile and whether that Moonlight version forwards the feature. Reconnect after adding or changing devices if necessary.

For background input, check Moonlight's background-controller option. For swapped Nintendo buttons, check client button-swap settings. Guide/Home/Share may also be handled by the client or Windows outside the game.

## Appendix: Moonlight touch, pen, and mobile keyboard

These are **screen-input features**, separate from controller support.

| Input type | What it is for | What to expect |
| --- | --- | --- |
| **Touchscreen used as a mouse** | Clicking and dragging on the remote desktop | The client turns gestures into mouse actions. This does not establish native multi-touch or pen-pressure support. |
| **Native screen touch** | Applications that accept Windows touch input | Requires native touch forwarding from the client and support in the Windows session. |
| **Native pen / stylus** | Handwriting and drawing in compatible applications | Pressure, tilt, eraser, and other pen data depend on what the hardware, client, and application support. |
| **Mobile on-screen keyboard** | Typing from a phone or tablet | Behavior depends on the client. In Avalon 1.1.0, soft-keyboard text can fail at Windows UAC prompts. |

For native touch or pen, leave Avalon's **Native Pen/Touch Support** enabled and select native forwarding in the client if offered. A client sending only mouse actions cannot supply pen pressure. Disabling native forwarding may still leave the client's mouse emulation available.

Moonlight features vary by platform and version: official release notes document [Android native stylus forwarding](https://github.com/moonlight-stream/moonlight-android/releases/tag/v12.0) and [PC native multi-touch](https://github.com/moonlight-stream/moonlight-qt/releases/tag/v5.0.0). Use the [Moonlight input guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#keyboardmousegamepad-input-options) and your client's settings; third-party clients may differ.

**Avalon 1.1.0 does not guarantee every physical pen, pressure/tilt behavior, UAC interaction, or multi-client pen/touch setup.** Validate your device and application before relying on it for drawing or handwriting. The native pen/touch option does not fix the mobile UAC keyboard limitation.

PlayStation controller touchpads use the controller features listed above; they are separate from screen touch and the Native Pen/Touch Support option.

For help, include your Avalon version, host Windows build, client name/version, device model, selected profile, and the affected feature. Do not share activation files, passwords, or pairing PINs.

Last reviewed for Avalon 1.1.0: **2026-11-15**.
