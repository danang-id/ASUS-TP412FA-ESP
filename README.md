> [!NOTE]  
> This ESP contains older version of OpenCore, your mileage may vary.

> [!IMPORTANT]  
> ASUS have multiple version of TP412FA model released with different specs (noticable by proccessor generation).
> This ESP works only for the model with exact speficiations bellow.

# ASUS TP412FA EFI System Partition (ESP)

This repository contains files and folder inside the EFI System Partition (ESP) on my ASUS TP412FA-EC302T notebook. 
This ESP contains OpenCore and other UEFI tools to boot to the operating systems I used, which are mainly macOS. 
Other operating systems, like Windows or Linux, are also supported with this OpenCore configuration.

# Disclaimer!
The OpenCore configuration used in *this ESP is tightly linked with my machine's BIOS firmware version and configuration*.
Any attempts to use this ESP &mdash;even on the same exact brand, model, hardware configuration, and BIOS firmware 
version&mdash; are **not guaranteed** to work as well as describe here.

## List of Contents
- [ASUS TP412FA EFI System Partition (ESP)](#asus-tp412fa-efi-system-partition-esp)
- [Disclaimer!](#disclaimer)
  - [List of Contents](#list-of-contents)
  - [Specification of ASUS TP412FA-EC302T](#specification-of-asus-tp412fa-ec302t)
  - [OpenCore Information](#opencore-information)
    - [UEFI Drivers Used](#uefi-drivers-used)
  - [[OS] macOS (Hackintosh)](#os-macos-hackintosh)
    - [SMBIOS and Supported macOS](#smbios-and-supported-macos)
    - [Works on macOS](#works-on-macos)
    - [Not Works / Problems on macOS](#not-works--problems-on-macos)
    - [macOS Kernel Extensions (Kext) Used](#macos-kernel-extensions-kext-used)
  - [[OS] Other Operating Systems](#os-other-operating-systems)
  - [Legal](#legal)

## Specification of ASUS TP412FA-EC302T
- **Processor**: Intel® Core™ i3-8145U (Whiskey Lake)
- **Chipset**: Intel® Cannon Point-LP
- **Integrated Graphic**: Intel® UHD Graphics 620
- **Discrette Graphic**: None
- **Memory**: 1 x 4 GB DDR4 2400MHz SDRAM (on-board)
- **Storage**: 1 x Intel 660P SSD 512GB PCIe® Gen3 x2 M.2
- **Audio**: Realtek ALC256
- **Wi-Fi**: Intel Wireless-AC 9560
- **Touchpad**: ELAN1300 I2C Interface
- **Touchscreen**: ELAN2097 I2C Interface
- **Biometric**: ELAN Fingerprint Reader
- **Screen Size**: 14 inches
- **Native Display Resolution**: 1920x1080
- **Input/Output (I/O)**: 
  - 1 x Intel USB 3.1 Gen 1 (Type C)
  - 1 x Intel USB 3.0 (Type A)
  - 2 x Intel USB 2.0 (Type A)
  - 1 x Intel HDMI out
  - 1 x Realtek SD card reader
  - 1 x AC adapter plug
  - 1 x Combo audio jack
  - 1 x Volume up/down button
- **Battery**: 3 cells polymer battery, 42 Watthours
- **BIOS Version**: TP412FA.310

## OpenCore Information
This ESP contains [OpenCore](https://github.com/acidanthera/OpenCorePkg) version 0.7.6. The boot mode used 
is **UEFI** with **CSM disabled** on **GUID Partition Table (GPT)** storage scheme.

### UEFI Drivers Used 
These are the UEFI drivers used by OpenCore.

- HfsPlus
- OpenRuntime
- OpenCanopy

## [OS] macOS (Hackintosh)
This ESP contains OpenCore configured to run the following macOS, including what are works and what are not works.

### SMBIOS and Supported macOS
This OpenCore configuration only support **macOS Big Sur (11)** (limited by APFS minimal version and 
minimal date). 

**MacBookPro15,4** is used as the SMBIOS of this configuration. Limited by SMBIOS, however, the possible macOS 
version supported ranges from macOS Mojave (10.15.4) up to the current macOS Monterey (12). 

If support for **macOS Catalina (10.15) and earlier** is required, set the APFS minimal version and minimal date
to the target macOS (the configuration value is available on OpenCore official documentation).

### Works on macOS
- [x] QE/CI Enabled Graphics of Intel® UHD Graphics 620
- [x] Screen brightness
- [x] Wi-Fi
- [x] Bluetooth
- [x] Touchpad
- [x] Touchscreen
- [x] Camera
- [x] Audio output
- [x] Audio input (internal microphone only)
- [x] Volume side keys
- [x] All USB Ports
- [x] Battery status indicator
- [x] HDMI out (video + audio)
- [x] Sleep, Shutdown, and Restart
- [x] Sleep and Wake with Lid

### Not Works / Problems on macOS
- [ ] Audio jack headset/speaker detection
- [ ] AC adapter state take some time to detect after state change (plug/unplug)
- [ ] Screen brightness *fn* keys (for brightness up and down)
- [ ] Fn keys
- [ ] Native card reader

### macOS Kernel Extensions (Kext) Used
OpenCore loads the kernel extensions with a configured order. Unless specified, this kernel extensions are loaded for 
macOS Mojave (10.14) up to the latest macOS Monterey (12).

1. USBPorts
2. AX88179-178A (for macOS Big Sur and later)
3. AX88179-178A-Legacy (for macOS Catalina and earlier)
4. Lilu
5. ECEnabler
6. WhateverGreen
7. VirtualSMC
8. SMCProcessor
9. SMCBatteryManager
10. SMCLightSensor
11. SMCSuperIO
12. AsusSMC
13. BrightnessKey
14. CPUFriend
15. CPUFriendDataProvider
16. NVMeFix
17. VoodooPS2Controller
18. VoodooPS2Controller/VoodooInput
19. VoodooPS2Controller/VoodooPS2Keyboard
20. VoodooI2C/VoodooGPIO
21. VoodooI2C/VoodooI2CServices
22. VoodooI2C
23. VoodooI2CHID
24. NoTouchID (for macOS Mojave only)
25. AppleALC
26. AirportItlwm_Mojave (for macOS Mojave only)
27. AirportItlwm_Catalina (for macOS Catalina only)
28. AirportItlwm_BigSur (for macOS Big Sur only)
29. AirportItlwm_Monterey (for macOS Monterey only)
30. IntelBluetoothInjector
31. IntelBluetoothFirmware

## [OS] Other Operating Systems
OpenCore is configured to support other operating systems as well. Tested on Windows 11, all 
components are working okay.

## Legal
This repository is owned and authored by **Danang Galuh Tegar Prasetyo** - [danang-id](https://github.com/danang-id),
and is licensed under the BSD 3-Clause License - see the [LICENSE.md](LICENSE.md) file for details.
