# UCE Tool

[简体中文](README.zh-CN.md) | **English** | [Deutsch](README.de.md) | [日本語](README.ja.md) | [Français](README.fr.md)

UCE Tool is the desktop companion for USB-C Explorer. It displays live measurements, reads E-Marker data, detects charging protocols, updates device firmware, and configures device theme colors.

It supports Windows 64-bit, Apple Silicon and Intel Macs, with Chinese, English, German, Japanese and French interfaces.

**[Download the latest release](https://github.com/Tamako-zz/UCE-Tool/releases/latest)** · **[All releases](https://github.com/Tamako-zz/UCE-Tool/releases)**

## Contents

- [Download and installation](#download)
- [Connect your device](#connect)
- [Dashboard and live chart](#dashboard)
- [E-Marker and records](#emarker)
- [Charging protocols and PDOs](#protocol)
- [Device firmware update](#firmware)
- [Device theme colors](#theme)
- [Language, appearance and device information](#settings)
- [Update UCE Tool](#software-update)
- [Troubleshooting](#faq)

<a id="download"></a>
## Download and installation

On the [Releases page](https://github.com/Tamako-zz/UCE-Tool/releases/latest), expand **Assets** and choose the file for your computer:

| File | Platform | Application |
| --- | --- | --- |
| `UCE-Windows-x64.zip` | Windows 64-bit, Intel / AMD | `UCE.exe` |
| `UCE-mac-arm64.dmg` | Mac, Apple Silicon (M series) | `UCE.app` |
| `UCE-mac-x86_64.dmg` | Mac, Intel | `UCE.app` |

On a Mac, check **Apple menu → About This Mac** to identify the processor.

**Windows:** Download the ZIP, extract it completely, and open `UCE.exe` from the extracted folder.

**macOS:** Open the matching DMG, drag `UCE.app` to **Applications**, eject the disk image, and open UCE from Applications. If macOS blocks the first launch, verify the source and allow it under **System Settings → Privacy & Security**.

<a id="connect"></a>
## Connect your device

You need a USB-C Explorer, a data-capable USB cable, and APP firmware compatible with your hardware. Theme and protocol features also require compatible firmware.

1. Start UCE Tool and connect the device through its data interface.
2. The application scans for devices and attempts to connect automatically. Confirm **Connected** on the left.
3. Open the desired page. The device card shows the name, abbreviated serial number and APP version; the full serial number is in Settings.

Click a device card to switch between connected devices. Wait until an upgrade finishes before switching. A device in **BOOT mode** can be recovered using firmware update; live measurements require running APP firmware.

<a id="dashboard"></a>
## Dashboard and live chart

Connect the device, open **Dashboard**, and click the start icon. The values and chart update as samples arrive.

| Channel | Meaning |
| --- | --- |
| VBUS / IBUS / POWER | Voltage (V), current (A), and power (W) |
| D+ / D− | USB data-line voltages |
| CC1 / CC2 | USB-C CC pin voltages |

Click channel labels to show or hide curves. Voltage, current and power have separate scales. Hover over the chart to inspect samples; `--` indicates no sample at that position.

Sampling rates are **1, 10, or 50 SPS**; the displayed time window is **10, 30, 60, or 120 seconds**. The stop control pauses acquisition; starting again resumes it without counting the paused time. Clear removes chart history and resets its elapsed time; if paused, start again to resume.

<a id="emarker"></a>
## E-Marker and records

Connect the cable to the indicated device port, open **E-Marker**, and click **Read** or **Continuous Read**. Before continuous detection, ensure no other powered devices are connected to the device output. Use the same button to stop continuous detection.

The cable page can show cable type, current, maximum voltage, USB speed, PD revision, TBT, EPR and length/latency when reported. Unreported or unrecognized fields show **Unknown**. Check the cable and connection if no E-Marker is detected. Raw VDO data appears below the illustration.

Successful readings are added to the current session's **Detection Records**. Export creates an `.xlsx` file with timestamps, cable information and raw VDOs. Times use UTC+8. Records are cleared when the application exits, so export anything you need to keep.

<a id="protocol"></a>
## Charging protocols and PDOs

Connect the charger or power source to the designated port, open **PD Detection**, and start detection. Voltage can rise during detection: disconnect any powered loads from the device output first. The same control can stop detection.

The page displays reported PDO voltage, current and power, together with individual passed, failed, pending or unsupported states. Available tests depend on device firmware. If the device is busy, stop the current detection before another operation.

<a id="firmware"></a>
## Device firmware update

This page updates firmware **on the USB-C Explorer device**.

1. Connect the device and open **Firmware Update**.
2. Click **Fetch releases** to load the version list.
3. Read the release notes and choose a version compatible with your hardware. If a version has multiple BIN files, choose the correct one according to its notes.
4. Click **Update** on that version. The selected firmware is downloaded, checked, and then sent to the device. The card shows progress and the result.

Only the selected firmware is downloaded; its temporary file is cleaned up after the operation. Keep USB connected and do not switch devices during the upgrade. After completion, refresh device information in Settings to check the APP version. If an upgrade fails, retain the error, check the connection and firmware compatibility, and retry.

<a id="theme"></a>
## Device theme colors

Open **Theme Configuration**. Use the arrows to switch preview pages, click editable color blocks, and use the background selector beneath the preview. **Apply to device** previews the colors; **Save to device** keeps them after a restart.

The preview covers measurements, statistics, E-Marker, protocol detection and device settings. Statistics color blocks represent the title, MAX, CUR, Ah and Wh areas. New configurable areas require device firmware support.

| Action | Effect |
| --- | --- |
| Restore defaults | Reset preview colors to defaults |
| Read from device | Replace the current preview with device colors |
| Apply to device | Preview on the device without permanent storage |
| Save to device | Apply and save colors across restarts |

Hover over the buttons for descriptions. If an area does not change on the device, check that its firmware supports that area.

<a id="settings"></a>
## Language, appearance and device information

Choose **简体中文, English, Deutsch, 日本語, or Français** under **Interface Language**. The choice is saved. It affects the desktop application, not the device display. Firmware notes use translations supplied by the publisher; raw device data remains unchanged.

Use the sidebar controls to switch light/dark appearance and collapse or expand navigation. Desktop appearance and device theme colors are configured separately. Settings also shows the device model, firmware, full serial number and production lot; refresh to read them again. Consult the activity log when reporting connection, detection or upgrade issues.

<a id="software-update"></a>
## Update UCE Tool

This updates the **desktop application**, not device firmware. In Windows use the top **About → Check for updates** menu; on macOS use **UCE → Check for updates** in the system menu.

Follow the prompt when a compatible update is available. Otherwise, open the release page and install the matching package manually after closing the old app. Finish any device firmware operation before updating the desktop application. Older Mac versions that do not support DMG updates require one manual installation of the newer app.

<a id="faq"></a>
## Troubleshooting

- **Device disconnected:** Check the data cable and USB port, close other serial tools, and verify the device is running compatible APP firmware. Check the activity log if the system recognizes the device but UCE Tool cannot connect.
- **No readings or chart:** Confirm the device is connected and start acquisition. Paused or BOOT mode devices do not produce live samples.
- **E-Marker fields show Unknown:** The cable or firmware may not report those fields. Check raw VDOs and other results.
- **GitHub request failed or was rate-limited:** Check network and proxy settings, try again later or use another network, and retain the full error when reporting a problem. An older Mac app with certificate errors should be replaced with a newer build containing the certificate fix.
- **Theme preview changes but the device does not:** Connect the device and apply or save the colors; check firmware support for the affected area. Use Save to keep colors after restart.
- **Which Mac download?** Use `arm64` for Apple Silicon and `x86_64` for Intel; check About This Mac.
- **An application update cannot be installed automatically:** Download the matching package from the release page and replace the old app after closing it.

When reporting an issue, include the OS version and processor, UCE Tool version, device hardware and APP firmware versions, steps to reproduce, full error or screenshot, and relevant activity logs.
