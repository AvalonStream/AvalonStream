# Avalon — Installation and Activation Guide

This guide explains how to install, configure, activate, troubleshoot, and uninstall Avalon on Windows.

**Before installing, read the system requirements and known issues in Sections 1–2.** Security software may interfere with Avalon, while ASTER and RDPWrap / `termsrv.dll`-related tools or patches have separate conflicts that must be resolved before use.

## Contents

1. [System Requirements](#1-system-requirements)
2. [Known Issues and Software Conflicts](#2-known-issues-and-software-conflicts)
3. [Antivirus and Windows Security](#3-antivirus-and-windows-security)
4. [Installing Avalon](#4-installing-avalon)
5. [First-Time Setup](#5-first-time-setup)
6. [Troubleshooting](#6-troubleshooting)
7. [License Activation](#7-license-activation)
8. [Uninstalling Avalon](#8-uninstalling-avalon)
9. [Additional Recommendations](#9-additional-recommendations)
10. [Support and Community](#10-support-and-community)

---

## 1. System Requirements

Avalon is designed for **64-bit Windows 10 and Windows 11**. Confirm the following requirements before installation.

| Requirement | Details |
|---|---|
| Operating system | Windows 10 / Windows 11 |
| Architecture | x64 (64-bit) only |
| Minimum Windows 10 version | Version 1903 (Build 18362) |
| Windows editions | Pro or compatible higher editions |
| Windows Home | **Not supported** |
| Windows 10/11 LTSC | Not fully tested |
| Windows IoT LTSC | Not fully tested |
| Windows on ARM | **Not supported** |
| Administrator privileges | Required for installation and removal |

### 1.1 Check Your Windows Version

1. Press `Win + R`.
2. Type `winver` and press **Enter**.
3. Check the Windows version and OS build against the requirements above.

You can also check your Windows edition and system architecture under **Settings → System → About**.

> **Important:** Windows 10 versions earlier than **1903** are not supported and may cause installation failures or unexpected behavior.

### 1.2 Windows Home Is Not Supported

If you use Windows 10 Home or Windows 11 Home, upgrade to Windows Pro or another compatible edition before installing Avalon. Installing on an unsupported edition may cause installation failures or session initialization problems.

See [Microsoft Support — Upgrade Windows Home to Windows Pro](https://support.microsoft.com/en-us/windows/deployment/install-upgrade/upgrade-windows-home-to-windows-pro). Complete and activate the Windows upgrade before installing Avalon.

### 1.3 LTSC and IoT LTSC Editions

Windows LTSC and Windows IoT LTSC editions have **not been comprehensively tested** with Avalon. Some configurations may work, but full compatibility, stability, and functionality are not guaranteed.

---

## 2. Known Issues and Software Conflicts

Review this list before installing Avalon and when troubleshooting unexpected behavior.

| No. | Software or Feature | Compatibility Note |
|---|---|---|
| 1 | **360 Security Guard (360 安全卫士)** | May cause compatibility issues with Avalon. |
| 2 | **Huorong Security (火绒杀毒)** | May cause compatibility issues with Avalon. |
| 3 | **QQ PC Manager (QQ 电脑管家)** | May cause compatibility issues with Avalon. |
| 4 | **Windows Security → Real-time protection** (Microsoft Defender Antivirus) | May interfere with Avalon components. |
| 5 | **Other antivirus or security software** | May also interfere with Avalon. |
| 6 | **ASTER multiseat software** | **Conflicts with Avalon. Do not use Avalon and ASTER at the same time.** |
| 7 | **RDP Wrapper (RDPWrap) and similar tools or patches involving `termsrv.dll`** | **Conflict with Avalon. Resolve the conflicting configuration before using Avalon.** |

**Entries 1–5 describe potential interference.** Their presence alone does not establish the cause of a failure. Check protection history, quarantine records, and relevant error messages before changing security settings.

**Entries 6–7 describe software conflicts.** Check these separately from antivirus interference, especially when instances cannot be created, started, or restarted.

### 2.1 Potential Interference from Security Software

Security software may block, quarantine, or restrict Avalon components without an obvious warning. Possible symptoms include:

- Installation, update, or uninstallation failures.
- Avalon services failing to initialize.
- Virtual display or driver problems.
- Instances failing to be created, started, or restarted.
- Previously working features becoming unavailable or behaving unexpectedly.

These issues may occur during setup, after an update, or after Avalon has been working normally for some time. Use the checks in **Section 3** to investigate security software interference.

### 2.2 Conflict with ASTER

**Avalon and ASTER cannot be used at the same time.** Resolve this conflict before installing or starting Avalon. If you need to disable or remove ASTER, use its documented procedures and restart Windows if prompted.

### 2.3 Conflicts with RDPWrap and `termsrv.dll`-Related Tools or Patches

**RDPWrap and similar tools or patches involving `termsrv.dll` conflict with Avalon.** Check for these tools or modifications before installation, including those applied before Avalon was installed.

Use the relevant tool's documented removal or restoration procedure to resolve the conflicting configuration, then restart Windows before retrying Avalon. Reinstalling Avalon alone should not be treated as a way to remove these conflicts.

---

## 3. Antivirus and Windows Security

Avalon interacts with Windows components to provide independent desktop sessions, virtual displays, and streaming. Microsoft Defender Antivirus, third-party security software, or Windows security policies may restrict these operations.

**Start by checking protection history and quarantine records.** When appropriate, use narrowly scoped exclusions or allowlist entries for verified Avalon components obtained from an official source. Temporarily pausing protection is a troubleshooting option when interference is suspected or confirmed; it is not a routine installation requirement.

### 3.1 Microsoft Defender Real-Time Protection

If real-time protection is interfering with an installation or uninstallation operation and a temporary pause is necessary:

1. Open **Start**, search for **Windows Security**, and open it.
2. Select **Virus & threat protection**.
3. Under **Virus & threat protection settings**, select **Manage settings**.
4. Set **Real-time protection** to **Off** and confirm any permission prompt.
5. Retry the affected operation.
6. **Turn real-time protection back on as soon as the operation or troubleshooting is complete.**

Settings path: **Windows Security → Virus & threat protection → Manage settings → Real-time protection**.

See [Microsoft Support — Virus and Threat Protection in Windows Security](https://support.microsoft.com/en-us/windows/security/threat-malware-protection/virus-and-threat-protection-in-the-windows-security-app).

> **Security notice:** Disabling real-time protection reduces protection against malicious software. Only consider this step for troubleshooting with a verified installer from an official Avalon source. Microsoft Defender may also automatically re-enable protection after a period of time.

### 3.2 Third-Party Security Software

For 360 Security Guard, Huorong Security, QQ PC Manager, or another security product:

1. Check its protection history, quarantine, and security events for blocked Avalon components.
2. Verify the affected files came from an official Avalon source before allowing or restoring them.
3. Use an exclusion or allowlist entry limited to the verified component where appropriate.
4. If necessary, temporarily pause the relevant protection using the product's supported controls and retry the affected operation.
5. Restore any protection you paused when troubleshooting is complete.

If a persistent incompatibility is confirmed, consider changing the conflicting security product while maintaining appropriate system protection. **Do not permanently leave the computer without active antivirus protection.**

If the issue continues, investigate the software conflicts in Section 2, Windows compatibility, driver restrictions, and the other checks in Section 6.

### 3.3 Virtual Display Drivers

Some Avalon releases, including **version 1.0.0**, use test-signed virtual display drivers rather than WHQL-certified drivers. Depending on the Windows security configuration, driver installation or loading may be restricted.

Disabling antivirus protection alone does not necessarily resolve driver-signing or Windows security policy restrictions. Record the exact driver error and consult the troubleshooting guidance before making further security changes.

---

## 4. Installing Avalon

Before running the installer, confirm that your Windows edition and architecture are supported, review Section 2, and resolve conflicts involving ASTER, RDPWrap, or `termsrv.dll`-related tools or patches.

### 4.1 Download the Installer

Download Avalon from an official source:

- [Official website](https://avalons.cc)
- [GitHub Releases](https://github.com/AvalonStream/AvalonStream/releases)

The installer filename follows the format `Avalon-Setup-x.x.x.exe`, where `x.x.x` is the version number.

### 4.2 Run the Installation Wizard

1. **Launch the installer.** Double-click `Avalon-Setup-x.x.x.exe` and approve the Windows administrator permission prompt.
2. **Choose a language.** You can change the interface language later in the Avalon Web Management Panel without reinstalling.
3. **Review the license agreement and notices.** Accept them to continue, or cancel if you do not agree.
4. **Choose an installation directory.** The default location is recommended for most users; a custom location is also available.
5. **Choose whether to create a desktop shortcut.** This is optional and does not affect core functionality.
6. **Select Install.** Allow the installer to finish configuring the required services, session components, and virtual display functionality. Do not interrupt the process.
7. **Restart if prompted.** Complete any requested Windows restart before proceeding to setup.

---

## 5. First-Time Setup

### 5.1 Open the Web Management Panel

Open a browser and visit:

`https://YOUR_HOST_IP:48080`

Replace `YOUR_HOST_IP` with the IP address of the Windows computer running Avalon. For example:

`https://192.168.1.100:48080`

Use **HTTPS** and port **48080**. If connecting from another device, make sure it can reach the Windows host over the network.

If the browser displays a certificate warning, verify that you are connecting to the intended Avalon host before proceeding. Keep the management interface accessible only from trusted networks.

### 5.2 Create Your Administrator Account

On first access, follow the on-screen instructions to set an administrator username, create a strong password, confirm your credentials, and complete initialization.

Keep these credentials secure; they protect access to the Avalon Web Management Panel.

### 5.3 Create and Start an Instance

1. **Create an instance** in the Web Management Panel.
2. Configure its display and other available settings.
3. **Start the instance.**
4. Pair the Moonlight client with the corresponding instance.
5. Connect through Moonlight to use the independent Windows desktop.

> **Note:** Creating an instance does not automatically start it. Start the instance before attempting to connect.

---

## 6. Troubleshooting

Check the known issues in Section 2 first, then use the guidance that matches your symptoms. Security software is one possible cause; Windows compatibility, drivers, host resources, and Avalon defects can also be involved.

### 6.1 Instances Cannot Be Created, Started, or Restarted

Check the following:

1. **Conflicting software:** Look for ASTER, RDPWrap, or `termsrv.dll`-related tools or patches. Resolve the conflicts described in Section 2 before retrying.
2. **Security software interference:** Review Microsoft Defender or third-party protection history and quarantine records, even if no warning appeared. Follow Section 3 if an Avalon component was blocked.
3. **Windows compatibility:** Confirm the Windows edition, architecture, version, and OS build against Section 1.
4. **Driver restrictions:** Check whether Windows rejected a required driver or prevented it from loading. Record the exact error.
5. **Incomplete installation:** Confirm that installation completed successfully with administrator privileges and that any requested restart was completed.
6. **Host resources and graphics drivers:** Review available resources, GPU drivers, and diagnostic information provided by Avalon.

### 6.2 The Web Management Panel Cannot Be Accessed

If `https://YOUR_HOST_IP:48080` does not open:

- Confirm that Avalon is installed and its required services are running.
- Check the host IP address, **HTTPS** scheme, and port **48080**.
- Check whether Windows Firewall or the network configuration is blocking the connection.
- If connecting from another device, verify network connectivity to the host.
- Review security software records to see whether Avalon was prevented from starting.

### 6.3 Reinstalling Avalon

Reinstalling may help with incomplete or interrupted installation, but it is not guaranteed to resolve every problem. Resolve known software conflicts before reinstalling.

1. Back up `license.dat` if Avalon has been activated, and save important settings.
2. Disconnect streaming clients and stop running Avalon instances.
3. Review the known issues in Section 2 and resolve any ASTER, RDPWrap, or `termsrv.dll`-related conflict.
4. Check protection history for blocked components. If security software is interfering, follow Section 3 before retrying the affected removal or installation operation.
5. Uninstall Avalon using the procedure in Section 8, and restart if prompted.
6. Download a fresh installer from an official source and run it with administrator privileges.
7. Complete any requested restart, open the Web Management Panel, and import your saved `license.dat` if needed.
8. Restore any security protections temporarily disabled during troubleshooting.

### 6.4 Report an Unresolved Issue

Search [Avalon GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues) for a matching report. Review any available workaround or update before opening a new issue.

Include:

- Avalon version.
- Windows edition, version, architecture, and OS build.
- CPU and GPU models.
- Antivirus or security software in use, and any relevant blocking events.
- Whether ASTER, RDPWrap, or `termsrv.dll`-related tools or patches are installed or have previously been used.
- A clear description of the problem and steps to reproduce it.
- Relevant error messages, screenshots, or diagnostic logs.
- Troubleshooting steps already attempted and their results.

**Do not publicly share passwords, CDKEYs, `license.dat` files, payment information, or links containing private access tokens.**

---

## 7. License Activation

Activate Avalon by purchasing a license through the official website or redeeming a CDKEY. Both methods use a `license.dat` file that you should keep for future restoration.

### 7.1 Method A — Purchase and Activate a License

#### Step 1 — Open the Purchase Page

In the Web Management Panel, select **More → Buy License** to open the official Avalon purchase page.

#### Step 2 — Enter Your Information and Complete Payment

Enter the required purchase information, including an accessible email address and your preferred payment method. A backup license file will be sent to that email after payment confirmation.

Select the purchase button, allow the checkout interface to load, and follow the payment instructions. Avoid repeatedly submitting the purchase request while it is loading.

#### Step 3 — Download `license.dat`

After payment is confirmed, you will be redirected to the license download page. Processing time can vary with the network connection and payment provider.

**The license download page is valid for 24 hours. Download `license.dat` promptly.**

If you close the page:

- **Before payment is complete:** Return to the purchase page and continue as appropriate.
- **After payment is complete:** Return to the license retrieval page within the 24-hour window, or use the backup copy sent to your purchase email. Check spam or junk folders if necessary.

#### Step 4 — Check Activation or Import the License

Return to the Web Management Panel and check the activation status. Avalon may automatically detect the completed purchase and activate the license.

If it has not activated automatically:

1. Download `license.dat` from the download page or purchase email.
2. Select **Import License** in the Web Management Panel.
3. Choose the file and follow the on-screen instructions.
4. Confirm that the activation status updates after validation.

Keep a secure backup of the file as described in Section 7.3.

### 7.2 Method B — Activate Using a CDKEY

1. Open the license management section of the Web Management Panel.
2. Select **Redeem CDKEY**.
3. Enter your CDKEY carefully and submit it.
4. If the key is valid and redemption succeeds, Avalon automatically activates the corresponding license.
5. Download or save `license.dat` when prompted, and keep a secure backup.

To restore the license after reinstalling Windows on the same licensed device, import the saved `license.dat` as described below; you do not need to repeat the original CDKEY redemption.

### 7.3 Back Up and Restore Your License

**Keep `license.dat` in secure private storage outside the Windows system drive**, such as a backup drive. Do not share the file publicly.

After reinstalling Avalon or Windows:

1. Install Avalon on the same licensed device.
2. Open the Web Management Panel.
3. Select **Import License** and choose your saved `license.dat`.
4. Follow the prompts and confirm the activation status.

The license is associated with the licensed device. Restoration on that device can use the saved file, including offline restoration where supported. Significant hardware changes, including changes to the motherboard or system drive, may affect activation.

---

## 8. Uninstalling Avalon

### 8.1 Before Uninstalling

1. Disconnect active streaming clients and stop running Avalon instances where possible.
2. Back up `license.dat` if Avalon has been activated.
3. Save any configuration information you want to retain.
4. If you have encountered blocked components, review Windows Security or antivirus records. Follow Section 3 if interference affects removal.

### 8.2 Remove Avalon

1. Open **Windows Settings**.
2. Go to **Apps → Installed apps** on Windows 11, or **Apps → Apps & features** on Windows 10.
3. Find Avalon and select **Uninstall**.
4. Follow the instructions and approve administrator permission prompts as needed.
5. Allow removal to finish and restart Windows if prompted.

Alternatively, use the Avalon uninstaller included with the installation, if available.

If removal fails, check for blocked components and consult Section 6 before retrying. **Restore any security protections temporarily disabled during removal.**

---

## 9. Additional Recommendations

- **Keep Windows and GPU drivers updated.** Use a supported Windows version with current security updates and review graphics driver updates for compatibility and performance improvements.
- **Use a reliable network.** Network quality affects streaming stability and latency.
- **Keep a license backup.** Retain `license.dat` after activation and before reinstalling Avalon or Windows.
- **Review security events.** Unexpected failures may involve quarantined files, restricted services, or driver-loading problems.
- **Check for software conflicts.** Review Section 2 when changing multiseat software or Remote Desktop tools and patches.
- **Protect the management interface.** Use a strong administrator password and keep the Web Management Panel on trusted networks.
- **Check configuration-specific compatibility.** Hardware, game anti-cheat systems, encoders, and Windows configurations may behave differently.
- **Review Avalon release notes.** New releases may include bug fixes, compatibility improvements, and additional features.

---

## 10. Support and Community

Use the official channels for downloads, bug reports, and feature suggestions:

- [Official website](https://avalons.cc)
- [GitHub repository](https://github.com/AvalonStream/AvalonStream)
- [Bug reports and issues](https://github.com/AvalonStream/AvalonStream/issues)
- [Latest releases](https://github.com/AvalonStream/AvalonStream/releases)

For an unresolved problem, include the information listed in Section 6.4 so maintainers can investigate it efficiently.
