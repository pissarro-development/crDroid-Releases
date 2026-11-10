# How to update ROM on Redmi Note 11 Pro+ 5G (pissarro)

This guide covers updating a ROM you already run to a newer release **without losing data**. For a clean/first install, see [`HowToInstallROM.md`](HowToInstallROM.md).

---

## When an update is possible

| From | To | Method |
| :--- | :--- | :--- |
| Any ROM | Different ROM | Clean flash ([`HowToInstallROM.md`](HowToInstallROM.md)) |
| Vanilla variant | GApps variant, or other way round | Clean flash ([`HowToInstallROM.md`](HowToInstallROM.md)) |
| Same ROM | Newer ROM revision (e.g. `rev.0` -> `rev.1`) | Update (this guide) |
| Same ROM | Newer ROM version | Update (this guide) |
| Same ROM | Newer Android version | Update (this guide) |

> Read **What's changed** and **Known issues** sections of new release first. If a release requires a clean flash, it says so there.

## Choosing a method

| Method | PC required | Custom kernel | GApps |
| :--- | :---: | :--- | :--- |
| A - Local update (OTA) | No | Removed, flash again via recovery afterwards | Kept if GApps package supports `addon.d` |
| B - ADB sideload | Yes | Flash again in same recovery session | Flash again in same recovery session |

## Prerequisites

- From release page of new ROM release: ROM package `<rom>.zip` and `<rom>.zip.sha256sum`
- A backup of your important data - an update keeps data, but nothing is guaranteed
- Method B only:
  - [Android SDK Platform-Tools](https://developer.android.com/tools/releases/platform-tools) (`adb` and `fastboot`) installed and added to PATH on your PC
  - GApps package you installed before (Vanilla builds with GApps only)
  - Kernel package you use (custom kernel users only)

---

## Step-by-step instructions

### 1. Verify checksum (Optional)

Put downloaded files in one folder, open a terminal there and run:

```bash
sha256sum -c <rom>.zip.sha256sum
```

Line must end with `OK`. On Windows, compare output of following command with contents of `.sha256sum` file:

```bash
certutil -hashfile <rom>.zip SHA256
```

Do not continue if checksum does not match - download file again.

### 2. Install update

Use **one** of methods below.

#### Method A - Local update (OTA)

Update is installed in background while ROM keeps running, then applied on reboot.

1. Copy ROM package `<rom>.zip` to internal storage of device.
2. Open **Settings** -> **System** -> **System updates**.
3. Select **Install local update** and choose ROM package.
4. Wait until installation completes. Do not reboot or power off device during installation.
5. Select **Reboot** when updater asks for it.

If updater reports a verification error, use Method B instead.

Update replaces boot image, so custom kernel and any root built into it are removed. To get them back, flash kernel package again following [`HowToInstallKernel.md`](HowToInstallKernel.md).

#### Method B - ADB sideload

1. Power off device completely.
2. Hold **Volume Up + Power** until recovery appears.
3. In recovery menu select **Apply update** -> **Apply from ADB**, then on your PC run:

```bash
adb sideload <rom>.zip
```

**Do not format data.** Terminal may stop at about 47% - this is normal. Wait until recovery reports that installation is complete.

4. If you use neither GApps nor a custom kernel, go to step 6. Otherwise recovery asks whether to reboot to recovery to install additional packages - select **Yes**.
5. ROM package replaces boot image, so custom kernel and any root built into it are removed by update. Select **Apply update** -> **Apply from ADB** and sideload each package, GApps first:

```bash
adb sideload <gapps>.zip
adb sideload <kernel>.zip
```

Select **Apply from ADB** again before each package. If recovery shows "Signature verification failed", select **Yes** to continue.

6. Return to main recovery menu and select **Reboot system now**.

### 3. First boot

First boot after an update may take several minutes.

---

## If device does not boot

1. Reboot into recovery (**Volume Up + Power**) and sideload same ROM package once more (Method B).
2. If it still does not boot, perform a clean flash following [`HowToInstallROM.md`](HowToInstallROM.md). This erases all data.

---

## Disclaimer

```
Flashing custom software carries real risk: bootloops, data loss, broken
hardware functionality and, in rare cases, an unrecoverable device.

You are choosing to make these modifications. Neither the maintainer of this
project nor the authors of the hosted software are responsible for anything
that happens to your device. Read the instructions, verify checksums, and
make backups.
```
