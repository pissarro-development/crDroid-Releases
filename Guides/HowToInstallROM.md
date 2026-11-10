# How to install ROM on Redmi Note 11 Pro+ 5G (pissarro)

This guide covers **clean flash**: installing ROM from stock firmware or switching from another ROM. To update ROM you already run, see [`HowToInstallUpdate.md`](HowToInstallUpdate.md).

> **Note:** `pissarro` covers Redmi Note 11 Pro+ 5G (GL), Redmi Note 11 Pro / Redmi Note 11 Pro+ (CN) and Xiaomi 11i family (IN). Double-check that your device matches before flashing anything.

---

## Prerequisites

- Unlocked bootloader
- [Android SDK Platform-Tools](https://developer.android.com/tools/releases/platform-tools) (`adb` and `fastboot`) installed and added to PATH on your PC
- USB cable that supports data transfer
- From release page of ROM:
  - Boot image `boot.img` and `boot.img.sha256sum`
  - ROM package `<rom>.zip` and `<rom>.zip.sha256sum`
- Optional:
  - Latest stock HyperOS firmware installed on device
  - Latest GApps package for Android 16

## Warnings

- **A clean flash erases all data on device**, including internal storage. Back up everything you need first.
- **Do not dirty flash** a different ROM on top of your current one. Within same ROM, follow [`HowToInstallUpdate.md`](HowToInstallUpdate.md) instead.
- Always use `boot.img` from **same release** as ROM package.

---

## Step-by-step instructions

### 1. Verify checksums (Optional)

Put all downloaded files in one folder, open a terminal there and run:

```bash
sha256sum -c boot.img.sha256sum
sha256sum -c <rom>.zip.sha256sum
```

Each line must end with `OK`. On Windows, compare output of following command with contents of `.sha256sum` file:

```bash
certutil -hashfile <file> SHA256
```

Do not continue if any checksum does not match - download file again.

### 2. Reboot into Fastboot

- Power off device completely.
- Hold **Volume Down + Power** until Fastboot screen appears.
- Connect device to your PC and check that it is detected:

```bash
fastboot devices
```

### 3. Flash boot image

Release `boot.img` contains ROM recovery. Flash it to boot partition:

```bash
fastboot flash boot boot.img
```

### 4. Reboot into Recovery

Wait until flashing completes, then reboot into recovery manually or with:

```bash
fastboot reboot recovery
```

### 5. Format data

In recovery menu select:

1. **Factory reset**
2. **Format data/factory reset**
3. **Format data**

Return to main menu once formatting completes.

### 6. Sideload ROM package

In recovery menu select:

1. **Apply update**
2. **Apply from ADB**

Then on your PC run:

```bash
adb sideload <rom>.zip
```

Terminal may stop at about 47% - this is normal. Wait until recovery reports that installation is complete.

### 7. Reboot into Recovery

After sideload completes, recovery asks whether to reboot to recovery to install additional packages. Select **Yes**.

### 8. Sideload GApps or other packages (Optional)

In recovery menu select **Apply update** -> **Apply from ADB**, then on your PC run:

```bash
adb sideload <package>.zip
```

If recovery shows "Signature verification failed", select **Yes** to continue. Repeat for every additional package.

### 9. Reboot into System

Return to main recovery menu and select **Reboot system now**. First boot may take several minutes.

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
