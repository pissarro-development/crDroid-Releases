# Flash Guide for Redmi Note 11 Pro+ 5G (pissarro)

## Prerequisites

- Unlocked bootloader
- ADB and Fastboot installed on your computer
- Compatible `boot.img` file
- ROM installation ZIP

## Flashing Instructions

### 1. Boot into Fastboot Mode

- Power off your device.
- Hold the appropriate key combination (typically **Volume Down + Power**) to enter Fastboot mode.

### 2. Flash the Boot Image

Connect your device to the computer via USB and run the following command:

```bash
fastboot flash boot boot.img
```

Wait for the process to complete, then reboot into recovery mode manually or using the following command:

```bash
fastboot reboot recovery
```

### 3. Apply Update via ADB

In the recovery menu: Select Apply update -> Choose Apply from ADB

Then on your computer, sideload the ROM ZIP package using:

```
adb sideload <rom-filename>.zip
```

### 4. Reboot into Recovery

After the sideload completes, the recovery will prompt you to reboot. Select Yes to reboot back into recovery.

### 5. Perform a Factory Reset

Once the device reboots into recovery again: Select Factory Reset -> Choose Format Data    

### 6 Flash GApps (optionally)

After formatting, you can flash GApps if you wish.

### 7. Final Reboot

After formatting or flashing GApps, return to the main recovery menu and select Reboot to system.

### 8. Done

Your device will now boot into system. The first boot may take several minutes.
