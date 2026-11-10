# crDroid for Redmi Note 11 Pro+ 5G (pissarro)

[![GitHub Total Downloads](https://img.shields.io/github/downloads/pissarro-development/crDroid-Releases/total?label=GitHub%20total%20downloads&style=for-the-badge&logo=github&color=181717)](https://github.com/pissarro-development/crDroid-Releases/releases)
[![SourceForge Total Downloads](https://img.shields.io/sourceforge/dt/pissarro-development/ROMs/crDroid?label=SourceForge%20total%20downloads&style=for-the-badge&logo=sourceforge&color=FF6600)](https://sourceforge.net/projects/pissarro-development/files/ROMs/crDroid/)

**Unofficial release and issue-tracking repository for crDroid on `pissarro`**

[![SourceForge Mirror](https://img.shields.io/badge/SourceForge-Mirror-FF6600?style=flat-square&logo=sourceforge)](https://sourceforge.net/projects/pissarro-development/files/ROMs/crDroid/)
[![Telegram Channel](https://img.shields.io/badge/Telegram-Channel-26A5E4?style=flat-square&logo=telegram)](https://t.me/pissarro_channel)
[![Telegram Group](https://img.shields.io/badge/Telegram-Group-26A5E4?style=flat-square&logo=telegram)](https://t.me/pissarro_hub)
[![Telegram Maintainer](https://img.shields.io/badge/Telegram-Maintainer-26A5E4?style=flat-square&logo=telegram)](https://t.me/z3rokwq)

---

## Device specifications

> **Note:** `pissarro` covers Redmi Note 11 Pro+ 5G (GL), Redmi Note 11 Pro / Redmi Note 11 Pro+ (CN) and Xiaomi 11i family (IN). Double-check that your device matches before flashing anything.

| Component | Specification |
| :--- | :--- |
| **SoC** | MediaTek Dimensity 920 (6 nm) |
| **CPU** | 2× Cortex-A78 @ 2.5 GHz + 6× Cortex-A55 @ 2.0 GHz |
| **GPU** | Mali-G68 MC4 |
| **Display** | 6.67" AMOLED, 1080 × 2400, 120 Hz |
| **Memory** | 6/8 GB RAM, 128/256 GB UFS 2.2 |
| **Battery** | 5160 mAh, 67W wired / 4500 mAh, 120W wired |
| **Camera** | 108 MP + 8 MP + 2 MP / 16 MP front |

## Releases

| Version | Revision | Android | Kernel | Status | Maintainer |
| :---: | :---: | :---: | :---: | :---: | :---: |
| [v10.14](https://github.com/z3rokwq/pissarro-releases/releases/tag/crdroid-10.14) | rev.0 | 14 | 4.14.y | Deprecated | [z3rokwq](https://github.com/z3rokwq) |
| [v11.7](https://github.com/z3rokwq/pissarro-releases/releases/tag/crdroid-11.7) | rev.0 | 15 | 4.14.y | Deprecated | [z3rokwq](https://github.com/z3rokwq) |
| [v12.5](https://github.com/pissarro-development/crDroid-Releases/releases/tag/v12.5_rev.0) | rev.0 | 16 QPR1 | 4.14.y | Deprecated | [z3rokwq](https://github.com/z3rokwq) |
| [v12.13](https://github.com/pissarro-development/crDroid-Releases/releases/tag/v12.13_rev.0) | rev.0 | 16 | 4.14.y | Active | [z3rokwq](https://github.com/z3rokwq) |

> **WIP** - in development | **Active** - maintained | **Deprecated** - no longer maintained

*Changelogs, known issues, required firmware, checksums, and build-specific flashing instructions are attached to each individual release on the [Releases](https://github.com/pissarro-development/crDroid-Releases/releases) page.*

## Installation

Step-by-step instructions are available in separate guides:
- *[`Guides/HowToInstallROM.md`](Guides/HowToInstallROM.md)* - clean install of a ROM
- *[`Guides/HowToInstallUpdate.md`](Guides/HowToInstallUpdate.md)* - update to a newer release without losing data
- *[`Guides/HowToInstallKernel.md`](Guides/HowToInstallKernel.md)* - install of a custom kernel

## Reporting issues

Bug reports for this project belong in the **[Issues](https://github.com/pissarro-development/crDroid-Releases/issues)** tab of this repository or in the **[Bugs topic](https://t.me/pissarro_hub/673)** of our Telegram group.

Before opening an issue, verify that you are on the latest release and using the firmware and kernel listed in its release notes. A useful report must include:
- Exact ROM version and build date
- Regional firmware version flashed prior to the ROM
- Recovery used and installation type (clean flash vs. dirty flash)
- Any root solution or third-party modules installed (Magisk / KernelSU / Zygisk)
- Relevant logs (`logcat` for userspace crashes, `dmesg` or `ramoops`/`expdb` for kernel panics and random reboots)

## Disclaimer

```
Flashing custom software carries real risk: bootloops, data loss, broken
hardware functionality and, in rare cases, an unrecoverable device.

You are choosing to make these modifications. Neither the maintainer of this
project nor the authors of the hosted software are responsible for anything
that happens to your device. Read the instructions, verify checksums, and
make backups.
```

## Credits

- **[z3rokwq](https://github.com/z3rokwq)** - maintainer of this repository
- All crDroid, kernel and recovery developers whose work these builds rely on - credit stays with them
