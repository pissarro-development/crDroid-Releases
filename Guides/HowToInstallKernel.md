# How to install kernel on Redmi Note 11 Pro+ 5G (pissarro)

> **Note:** `pissarro` covers Redmi Note 11 Pro+ 5G (GL), Redmi Note 11 Pro / Redmi Note 11 Pro+ (CN) and Xiaomi 11i family (IN). Double-check that your device matches before flashing anything.

---

## Prerequisites

- Unlocked bootloader
- Any custom recovery (AOSP recovery, OrangeFox, TWRP, etc.)
- A ROM listed as compatible in **Compatibility** table of kernel release page
- [Android SDK Platform-Tools](https://developer.android.com/tools/releases/platform-tools) (`adb` and `fastboot`) installed and added to PATH on your PC
- Kernel package from release page: one kernel package `<kernel>.zip` and its `<kernel>.zip.sha256sum`
- Boot image `boot.img` from release of your current ROM, to restore default kernel if something goes wrong

## Choosing a variant

| Variant | Root solution | Root manager app |
| :--- | :--- | :--- |
| Vanilla | None built in, Apatch can be used | - |
| KernelSU | KernelSU with SUSFS | KernelSU |
| KernelSU-Next | KernelSU-Next with SUSFS | KernelSU-Next |
| BakaSU | BakaSU with SUSFS | BakaSU |

> Use root manager app version linked in **Variants** column of release page. Do not combine a KernelSU-based variant with APatch or Magisk.

---

## Step-by-step instructions

### 1. Verify checksum (Optional)

Put downloaded files in one folder, open a terminal there and run:

```bash
sha256sum -c <kernel>.zip.sha256sum
```

Line must end with `OK`. On Windows, compare output of following command with contents of `.sha256sum` file:

```bash
certutil -hashfile <kernel>.zip SHA256
```

Do not continue if checksum does not match - download file again.

### 2. Reboot into Recovery

- Power off device completely.
- Hold **Volume Up + Power** until recovery appears.

### 3. Flash kernel package

**Option A - ADB sideload**:

In recovery menu select **Apply update** -> **Apply from ADB**, then on your PC run:

```bash
adb sideload <kernel>.zip
```

If recovery shows "Signature verification failed", select **Yes** to continue.

**Option B - from internal storage**:

Copy kernel package to device beforehand, select **Install**, choose package and swipe to confirm.

### 4. Reboot into System

Return to main recovery menu and select **Reboot system now**. First boot may take slightly longer than usual.

---

## If device does not boot

Reboot into Fastboot (**Volume Down + Power**) and flash `boot.img` from release of your current ROM to restore default kernel:

```bash
fastboot flash boot boot.img
fastboot reboot
```

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
