# Avalon — Installation & Activation Guide

Welcome to **Avalon**!

This guide will walk you through everything you need to know about installing, configuring, activating, troubleshooting, and uninstalling Avalon on Windows.

Before proceeding, we strongly recommend reading the system requirements and security software compatibility notes below. A few minutes of preparation can save you a considerable amount of troubleshooting later.

---

## 1. System Requirements

Avalon is designed for **64-bit Windows 10 and Windows 11** systems.

Please verify that your operating system meets the following requirements before installation.

| Requirement | Details |
|---|---|
| Operating System | Windows 10 / Windows 11 |
| Architecture | x64 (64-bit) only |
| Minimum Windows 10 Version | Version 1903 (Build 18362) |
| Windows Editions | Pro or compatible higher editions |
| Windows Home | **Not Supported** |
| Windows 10/11 LTSC | Not fully tested |
| Windows IoT LTSC | Not fully tested |
| Windows on ARM | Not Supported |
| Administrator Privileges | Required for installation and removal |

### 1.1 Check Your Windows Version

To check your Windows version:

1. Press `Win + R` on your keyboard.
2. Type `winver` and press **Enter**.
3. A window will appear showing your Windows version and OS build number.
4. Make sure your system meets the minimum requirements listed above.

You can also check your Windows edition and system architecture under:

**Settings → System → About**

> **Important:** Windows 10 must be version **1903 or newer**. Earlier versions are not supported and may result in installation failures or unexpected behavior.

### 1.2 Windows Home Edition Is Not Supported

Unfortunately, Avalon does not currently support Windows Home editions.

If you are using Windows 10 Home or Windows 11 Home, you must upgrade to Windows Pro or another compatible edition before installing Avalon.

Attempting to install Avalon on an unsupported edition may result in installation failures, session initialization problems, or other unpredictable behavior.

For official instructions on upgrading Windows Home to Pro, please refer to Microsoft's documentation:

**[Microsoft Support — Upgrade Windows Home to Windows Pro](https://support.microsoft.com/en-us/windows/deployment/install-upgrade/upgrade-windows-home-to-windows-pro)**

Please ensure that your Windows upgrade is successfully completed and activated before attempting to install Avalon.

### 1.3 About LTSC and IoT LTSC Editions

Some users may prefer Windows LTSC or Windows IoT LTSC editions for their reduced background activity and long-term servicing characteristics.

However, these editions have **not been comprehensively tested** with Avalon.

Although Avalon may work on some LTSC configurations, we cannot guarantee full compatibility, stability, or functionality.

If you decide to use Avalon on an LTSC-based system, please be aware that you are doing so at your own discretion.

---

## 2. Important: Antivirus & Windows Security Compatibility

**Please read this section carefully before installing or uninstalling Avalon.**

Avalon interacts with several Windows system components to provide independent desktop sessions, virtual displays, and streaming functionality.

Due to the nature of these operations, Microsoft Defender Antivirus, Windows Security policies, or third-party antivirus software may occasionally interfere with certain Avalon components.

In some cases, security software may silently block, quarantine, or restrict a component without displaying an obvious warning.

This can lead to unexpected problems, including but not limited to:

- Installation or uninstallation failures.
- Avalon services failing to initialize.
- Virtual display or driver-related problems.
- Instances failing to be created or started.
- Instances failing to restart correctly.
- Previously working features suddenly becoming unavailable.
- Unexpected behavior during normal operation.

These problems may occur during installation, after updating, or even after Avalon has been working normally for some time.

**Security software interference is one of the first things worth investigating when Avalon behaves unexpectedly.** However, it is not the only possible cause.

### 2.1 Microsoft Defender Real-Time Protection

For a smoother installation or uninstallation experience, you may need to temporarily disable Microsoft Defender real-time protection if it is interfering with Avalon.

We recommend checking protection history and using narrowly scoped exclusions for trusted Avalon components whenever possible.

If temporarily disabling real-time protection is necessary, follow these steps:

1. Open the Windows **Start** menu.
2. Search for and open **Windows Security**.
3. Select **Virus & threat protection**.
4. Under **Virus & threat protection settings**, click **Manage settings**.
5. Locate **Real-time protection**.
6. Switch the setting to **Off**.
7. Confirm the Windows permission prompt if one appears.

You can now retry the affected installation or uninstallation operation.

For Microsoft's official instructions, see:

**[Microsoft Support — Virus and Threat Protection in Windows Security](https://support.microsoft.com/en-us/windows/security/threat-malware-protection/virus-and-threat-protection-in-the-windows-security-app)**

> **Security Notice**
>
> Disabling real-time protection reduces your system's protection against malicious software.
>
> Only consider this step when using an installer obtained from an official Avalon source and when troubleshooting a confirmed or suspected compatibility issue.
>
> Re-enable real-time protection as soon as installation or troubleshooting is complete.
>
> Microsoft Defender may also automatically re-enable protection after a period of time.

### 2.2 Third-Party Antivirus Software

If you are using a third-party antivirus or endpoint security product, similar compatibility issues may occur.

Depending on your security software, you may consider:

- Adding verified Avalon executables or components to the antivirus exclusion or allowlist.
- Checking quarantine and security event history for blocked Avalon components.
- Temporarily pausing antivirus protection during installation or uninstallation, if necessary.
- Temporarily exiting the antivirus application when its protection can be safely paused.
- If persistent incompatibility is confirmed, considering a different security product or uninstalling the conflicting one while maintaining appropriate system protection.

**We do not recommend permanently leaving your computer without active antivirus protection.**

If problems persist even after antivirus interference has been ruled out, other Windows security policies, driver restrictions, or compatibility issues may be responsible.

### 2.3 A Note About Virtual Display Drivers

Some Avalon releases, including version 1.0.0, use test-signed virtual display drivers rather than WHQL-certified drivers.

Depending on your Windows security configuration, driver installation or loading may be restricted.

Disabling antivirus protection alone will not necessarily resolve driver-signing or Windows security policy restrictions.

If Windows reports a driver-related error, please record the exact message and consult the troubleshooting section before making additional system security changes.

---

## 3. Installing Avalon

Once you have confirmed that your system meets the requirements, you are ready to install Avalon.

### Step 1 — Download the Installer

Download the latest Avalon installer from an official source:

- **Official Website:** https://avalons.cc
- **GitHub Releases:** https://github.com/AvalonStream/AvalonStream/releases

The installer filename follows this format:

`Avalon-Setup-x.x.x.exe`

Here, `x.x.x` represents the version number.

We strongly recommend obtaining the installer only from official distribution channels.

### Step 2 — Launch the Installer

Double-click the downloaded installer:

`Avalon-Setup-x.x.x.exe`

If Windows requests administrator privileges, approve the prompt to continue.

Administrator permissions are necessary because Avalon installs and configures components that interact with Windows at the system level.

### Step 3 — Choose Your Language

Select your preferred language from the installation wizard.

Don't worry if you accidentally select the wrong language!

**You can change the interface language later from the Avalon Web Management Panel.**

There is no need to reinstall Avalon just to change its display language.

### Step 4 — Review the License Agreement

Carefully read the license agreement and any additional notices displayed by the installer.

If you understand and agree to the terms, accept the agreement and continue.

If you do not agree, cancel the installation.

### Step 5 — Choose an Installation Directory

Select the directory where Avalon should be installed.

You may use the default installation path or choose a custom location according to your preferences.

For most users, the default installation directory is recommended.

### Step 6 — Desktop Shortcut

Choose whether you would like the installer to create a desktop shortcut.

This is entirely optional and does not affect Avalon's core functionality.

### Step 7 — Complete the Installation

Click **Install** and allow the installer to complete the required operations.

During installation, Avalon may configure services, session-related components, and virtual display functionality.

Please avoid interrupting the installation process.

Once the installer reports that installation has completed successfully, you can proceed to the initial setup.

If Windows or the installer requests a restart, complete it before continuing.

---

## 4. First-Time Setup

Congratulations! Avalon should now be installed on your Windows host.

The next step is to open its Web Management Panel and initialize your administrator account.

### 4.1 Open the Web Management Panel

Open a web browser and navigate to:

`https://YOUR_HOST_IP:48080`

Replace `YOUR_HOST_IP` with the IP address of the Windows computer running Avalon.

For example:

`https://192.168.1.100:48080`

Make sure you are using **HTTPS** and the correct port number, **48080**.

If accessing Avalon from another device, ensure that the device can reach your Windows host over the network.

If your browser displays a certificate warning, verify that you are connecting to your intended Avalon host before proceeding.

For security reasons, we recommend keeping the management interface accessible only from trusted networks.

### 4.2 Create Your Administrator Account

When accessing Avalon for the first time, you will be prompted to configure your administrator credentials.

Follow the on-screen instructions to:

1. Set your administrator username.
2. Create a secure password.
3. Confirm your credentials.
4. Complete the initialization process.

**Please remember your username and password.**

These credentials protect access to the Avalon Web Management Panel.

### 4.3 Start Using Avalon

After initialization, you will be able to access the Avalon management interface.

From here, you can begin managing your desktop instances.

The basic workflow is:

1. **Create an instance** using the Web Management Panel.
2. Configure the instance's display and other available settings.
3. **Start the instance** after creation.
4. Pair your Moonlight client with the corresponding instance.
5. Connect using Moonlight and enjoy your independent Windows desktop.

> **Note:** Creating an Avalon instance does not automatically start it. Make sure the instance is running before attempting to connect.

That's it!

**Your Avalon environment is now ready to use.**

One Windows host. Multiple independent desktop experiences.

---

## 5. Troubleshooting Installation & Runtime Issues

Although we aim to make Avalon as reliable and straightforward as possible, compatibility problems can occasionally occur due to the complexity of Windows session management, drivers, hardware, and security software.

If you encounter problems, please don't panic.

The following recommendations may help.

### 5.1 Instances Cannot Be Created, Started, or Restarted

If an instance fails to initialize, start, or restart correctly, investigate the following possibilities:

1. **Antivirus interference:** Check whether Microsoft Defender or another security application has blocked or quarantined any Avalon component.
2. **Windows compatibility:** Confirm your Windows edition, architecture, and build number.
3. **Driver restrictions:** Check whether Windows has rejected or prevented a required driver from loading.
4. **Incomplete installation:** Verify that Avalon was installed successfully with administrator privileges.
5. **Resource or compatibility issues:** Review available host resources, GPU drivers, and any diagnostic information provided by Avalon.

Security software may interfere silently, so it is worth reviewing its protection history even when no obvious warning appeared.

However, please do not assume every failure is caused by antivirus software.

### 5.2 The Web Management Panel Cannot Be Accessed

If `https://YOUR_HOST_IP:48080` does not open, check the following:

- Confirm that Avalon is installed and its required services are running.
- Verify that you entered the correct host IP address.
- Make sure you are using HTTPS rather than HTTP.
- Confirm that port `48080` is correct.
- Check that your Windows Firewall or network configuration is not blocking the connection.
- If accessing the panel from another computer, verify network connectivity between both devices.

Also check whether your antivirus software has prevented Avalon from starting normally.

### 5.3 Reinstalling Avalon

If the installation appears corrupted or important components continue to malfunction, a complete reinstall may help.

Before reinstalling:

1. Back up your `license.dat` file if Avalon has been activated.
2. Save any important settings or information you may need later.
3. Stop active Avalon instances and disconnect streaming clients.
4. Review antivirus protection history and investigate any blocked components.
5. Uninstall Avalon using its normal uninstallation procedure.
6. If a security product is confirmed to be interfering, temporarily adjust its protection settings as described earlier.
7. Download a fresh copy of the Avalon installer from an official source.
8. Run the installer with administrator privileges.
9. Restore your license using the Web Management Panel if necessary.
10. Re-enable any security protections you temporarily disabled.

A clean reinstall may resolve issues caused by incomplete component registration, interrupted setup operations, or security software interference.

**However, reinstalling Avalon is not guaranteed to resolve every problem.**

### 5.4 Still Not Working? Report an Issue

If the problem persists even after following the troubleshooting steps, it may be caused by an Avalon software defect, an unsupported configuration, or another issue that has not yet been identified.

As with any software involving complex system-level operations, bugs can occasionally occur.

We welcome bug reports and feedback from the community.

Please visit our GitHub Issues page:

**[Avalon — GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues)**

Before creating a new issue:

1. Search existing issues to see whether someone has already reported the same problem.
2. If a matching issue exists, review any available solutions or updates.
3. If no matching issue exists, create a new issue describing your problem.

When reporting a bug, please include as much relevant information as possible:

- Avalon version.
- Windows edition, version, and OS build.
- CPU and GPU models.
- Antivirus or security software in use.
- A clear description of the problem.
- Steps required to reproduce the issue.
- Relevant error messages, screenshots, or diagnostic logs.

**Do not publicly share passwords, CDKEYs, `license.dat` files, payment information, or links containing private access tokens.**

Providing detailed information will help the maintainers and community understand and investigate the issue more efficiently.

Please allow some time for a maintainer or community member to respond.

Your feedback helps us improve Avalon for everyone.

---

## 6. License Activation

Avalon supports multiple license activation methods.

Depending on how you obtain your license, you can activate Avalon by purchasing a license through the official website or redeeming a CDKEY.

Please read the appropriate section below.

### 6.1 Method A — Purchase and Activate a License

If you would like to purchase an Avalon license, you can initiate the purchase directly from the Web Management Panel.

#### Step 1 — Open the Purchase Page

In the Avalon Web Management Panel, navigate to:

**More → Buy License**

You will be redirected to the official Avalon purchase page.

#### Step 2 — Enter Your Purchase Information

On the purchase page, provide the required information, including:

- Your email address.
- Your preferred payment method.
- Any other information required by the checkout process.

**Please enter a valid email address that you can access.**

Your email address is important because a backup copy of your license will be delivered there after successful payment.

#### Step 3 — Complete Payment

Click the purchase button on the official website.

A secure checkout interface will appear.

Depending on your network connection, it may take a few moments for the checkout interface to load.

Please avoid repeatedly submitting the purchase request while the page is loading.

Follow the payment instructions and complete your purchase.

#### Step 4 — Download Your License

After your payment has been successfully processed, please allow some time for the system to confirm your transaction.

Processing times may vary depending on your network connection and payment provider.

Once the payment is confirmed, you will be redirected to a **License Download Page**.

From this page, you can download your license file:

`license.dat`

**Important: The license download page remains valid for 24 hours.**

We strongly recommend downloading your license immediately after completing your purchase.

#### Step 5 — What If You Accidentally Close the Page?

Don't worry!

If you accidentally close the page before completing your purchase, you can return to the purchase page and continue as appropriate.

If payment has already been completed, you can return to the license retrieval page while the corresponding 24-hour download window remains valid.

For additional protection against accidental data loss, the Avalon licensing system also sends a backup copy of your `license.dat` file to the email address provided during checkout after receiving successful payment confirmation.

If you cannot find the email, please check your spam or junk folder.

This ensures that you have an additional way to retrieve your license even if you accidentally close the download page.

#### Step 6 — Activate Avalon

After purchasing your license, return to the Avalon Web Management Panel.

In some cases, Avalon may have already detected your successful purchase and **automatically activated your license**.

If your license is already active, no further action is required.

If Avalon has not activated automatically, you can activate it manually:

1. Download `license.dat` from the license download page or your purchase confirmation email.
2. Open the Avalon Web Management Panel.
3. Find the **Import License** option.
4. Select your `license.dat` file.
5. Follow the on-screen instructions to complete activation.

Once the license has been successfully imported and validated, Avalon should display the updated activation status.

#### Step 7 — Keep Your License File Safe

**Please keep a secure backup of your `license.dat` file.**

This file is important for restoring your license after reinstalling Avalon or Windows.

We recommend storing it in a safe location outside your Windows system drive, such as a personal backup drive or secure private storage.

Your license is associated with the licensed device. Reinstalling Windows on the same device can be supported using the saved license file, but significant hardware changes, including changes to the motherboard or system drive, may affect activation.

Do not share your license file publicly.

---

### 6.2 Method B — Activate Using a CDKEY

If you have received a valid Avalon CDKEY, the activation process is straightforward.

#### Step 1 — Open the Web Management Panel

Open the Avalon Web Management Panel and locate the license management section.

Click:

**Redeem CDKEY**

#### Step 2 — Enter Your CDKEY

Enter the CDKEY you received into the provided input field.

Make sure the key has been entered correctly.

Submit the key to begin the redemption process.

If your CDKEY is valid and the redemption succeeds, Avalon will automatically activate the corresponding license.

#### Step 3 — Save Your License File

After successful CDKEY redemption, Avalon will prompt you to download or save a file named:

`license.dat`

**Please make sure you save this file and keep a backup.**

This step is extremely important.

Your `license.dat` file serves as a reusable local license file for the licensed device.

#### Step 4 — Restore Your License After Reinstalling Windows

If you reinstall Windows in the future, you do not need to repeat the original CDKEY redemption process to restore the license on the same licensed device.

Instead:

1. Reinstall Avalon on your Windows system.
2. Open the Avalon Web Management Panel.
3. Navigate to **Import License**.
4. Select your previously saved `license.dat` file.
5. Import the file and complete the activation process.

Your license can be restored using the saved file, including offline restoration on the same licensed device where supported.

Please note that significant hardware changes may affect device-bound license validity.

---

## 7. Uninstalling Avalon

If you decide to uninstall Avalon, we recommend preparing your system before removal.

### Before Uninstalling

1. Disconnect active streaming clients and stop running Avalon instances where possible.
2. Back up your `license.dat` file if you have activated Avalon.
3. Save any important configuration information you wish to preserve.
4. Review Windows Security or antivirus settings if you have previously encountered component-blocking issues.

If security software interferes with the uninstallation process, you may temporarily adjust its protection settings using the guidance in Section 2.

### Uninstallation Procedure

1. Open **Windows Settings**.
2. Navigate to **Apps → Installed apps** on Windows 11, or **Apps & features** on Windows 10.
3. Locate Avalon in the installed application list.
4. Select **Uninstall** and follow the instructions.

Alternatively, use the Avalon uninstaller provided with your installation, if available.

Allow the removal process to finish and restart Windows if prompted.

If uninstallation fails, consult the troubleshooting section and check for blocked components before trying again.

**Remember to restore any security protections that were temporarily disabled during the removal process.**

---

## 8. Additional Notes & Recommendations

For the best possible Avalon experience, please keep the following points in mind:

- **Keep Windows updated.** Supported Windows versions with current security updates are recommended.
- **Keep your GPU drivers updated.** Graphics drivers can significantly affect streaming compatibility and performance.
- **Use a reliable network.** Network quality can directly affect streaming stability and latency.
- **Keep a license backup.** Always retain a copy of `license.dat` after activation.
- **Review security software warnings.** Unexpected failures may be related to quarantined files, restricted services, or driver-loading problems.
- **Protect the management interface.** Use a strong administrator password and avoid exposing the Web Management Panel directly to untrusted networks.
- **Check compatibility before reporting a bug.** Some hardware, game anti-cheat systems, encoders, and Windows configurations may behave differently.
- **Stay informed.** New Avalon releases may contain important bug fixes, compatibility improvements, and additional features.

---

## 9. Support & Community

If you need help, discover a bug, or would like to suggest a new feature, you are welcome to participate in our community.

**Official Website:** https://avalons.cc

**GitHub Repository:** https://github.com/AvalonStream/AvalonStream

**Bug Reports & Issues:** https://github.com/AvalonStream/AvalonStream/issues

**Latest Releases:** https://github.com/AvalonStream/AvalonStream/releases

We appreciate every bug report, suggestion, and contribution.

Avalon is continuously evolving, and community feedback plays an important role in helping us improve stability, compatibility, and the overall user experience.

Thank you for choosing Avalon!

**One Host. Multiple Instances. Endless Possibilities.**
