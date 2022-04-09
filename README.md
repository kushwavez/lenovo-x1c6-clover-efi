#  Lenovo ThinkPad X1 Carbon 6th Gen [Monterey 12 - Windows 11]
## Clover EFI for Lenovo ThinkPad X1 Carbon 6th Gen - macOS Monterey 12
## Insanelymac: [[GUIDE] Lenovo ThinkPad X1 Carbon 6th Gen [Monterey 12 - Windows 11]](https://www.insanelymac.com/forum/topic/346368-guide-lenovo-thinkpad-x1-carbon-6th-gen-big-sur-11-windows-10/)
<p align="center">
<img src="https://i.ibb.co/MNcPxHf/lenovo-x1c6.png">
</p>
<p align="center"><b>Lenovo ThinkPad X1 Carbon 6th Gen</b></p>
<p>Specifications:</p>

- BIOS: v1.50
- CPU: i7-8650U (Kaby Lake-R, 2.1 GHz up to 4.2 GHz, Quad-Core)
- GPU: Intel UHD 620
- Display: WQHD 2560x1440 (non-touch) 14" 300 nit
- RAM: 16 GB (2x8) DDR3 2133MHz
- Audio: ALC3286
- SSD: WDC PC SN720 SDAQNTW-512G-1001
- WiFi & Bluetooth: Intel AC-8265 M.2 (replaced to BCM94360CS2 with NGFF M.2 adapter)
- Fingerprint reader
- HD webcam
- Multigesture SMBus/RMI Synaptics touchpad with 3 buttons
- 2 level Backlight keyboard
- 57 Whr Battery
- Connectors:
  - 2x USB-Type C - Thunderbolt 3
  - 2x USB 3.1 Gen 1 (1x USB charging)
  - 1x Ethernet dongle (Intel I219V4 PCI-e)
  - 1x HDMI
  - 3.5mm combo-jack audio
  
<p align="center">
<img src="https://user-images.githubusercontent.com/33935034/150013996-2dec891d-1bbd-46c8-98a0-ab5eea56858b.png">
</p>

## BIOS settings:
- Secure Boot: Disabled
- UEFI: Enabled
- CSM: Disabled
- Virtualization, VT-d: Enabled
- Hyper-Threading: Enabled
- Anti-Theft: Disabled
- Intel SGX: Software Controlled
- Disable Fingerprint at I/O
- Thunderbolt device: Enabled
- For Thunderbolt 3 hot-plug (higher power consumption):
  - Thunderbolt BIOS Assist Mode: Disabled
  - Security Level: No security
  - Support in Pre Boot Environment: Disabled
- For Thunderbolt 3 without hot-plug (lower power consumption but need to plug your device before boot)
  - Thunderbolt BIOS Assist Mode: Enabled

## What is working?
- AirDrop, Handoff (only with Broadcom cards)
- iCloud, Messages, App Store, FaceTime, etc.
- Instant WiFi Hotspot with iPhone (only with original Apple Broadcom cards, such as BCM94360CS2)
- Intel UHD 620 (QE/CI, hardware decode/encode, VP9, HDMI)
- Sound (incl. combo-jack, HDMI out)
- Thunderbolt 3 (with hot-plug support)
- USB ports
- Ethernet dongle
- TrackPad, TrackPoint and Keyboard (incl. native multi-gestures, FN keys)
- FileVault
- Battery (~0.5 W when TB3 hot-plug is disabled, ~2W when enabled)
- Sleep
- Power Management
- Webcam
- SD card reader

## What isn't working?
- Fingerprint reader
- Hibernation
  - I think it's fixable, but just not worth the trouble for me. Just use normal sleep (hibernationmode=3) like on real MacBooks
- Original Samsung PM NVMe SSD
  - Causing kernel panics. Not fixable, replace your drive with an aftermarket one. I used KINGSTON A2000 and WDC PC SN720, but feel free to choose anything other than Samsung
  
## Issues:
- With Intel wifi the Bluetooth is not functioning properly, AirDrop is not working. Recommended to replace it with an original Apple BCM94360CS2 card to get fully-working functionality like on real Macs
- HDMI isn't working if you start the system with plugged in, disconnect before start and reconnect it after macOS is up and running. 
  - Fixable with EDID patch
- HDMI breaks after sleep/wake, need to re-plug
  - Fixable with EDID patch
- Audio sometimes just goes blank at random (rarely): A quick lid close/open solves this, issue needs to be debugged and reported to the Acidanthera team
- Thunderbolt 3 (I only have an ADT-Link R43SG-TB3 device with RX 470, so maybe other devices are good, but I don't have more TB3 devices to test with):
  - If you disconnect the eGPU the notebook will freeze (high CPU usage), you need to restart
  - After sleep hot-plug is not working with the TB3 eGPU (device not detected)
    - Workaround: Plug the TB3 in, put the notebook into sleep, wake it up. It may fail sometimes, try it again if that is the case


## Installation:
- Create a macOS USB Installer with any method you now.
    - For creating Monterey Installer USB on Windows, use my guide: <a href="https://www.insanelymac.com/forum/topic/346703-guide-creating-clover-macos-big-sur-installer-usb-on-windows/" target="_blank">[GUIDE] Creating Clover macOS Monterey Installer USB on Windows</a>
    - On macOS you can download the macOS Installer from App Store, or with <a href="https://github.com/corpnewt/gibMacOS" target="_blank">gibMacOS</a>, and create the USB Installer with the official <a href="https://support.apple.com/en-in/HT201372" target="_blank">"createinstallmedia"</a> method
    - On Windows you can create High Sierra - Catalina Installer USB with gibMacOS
- Mount your USB’s EFI and paste my CLOVER and BOOT folder from my bootpack
folder to it
    - On Windows you can mount your USB’s EFI with MiniTool Partition Wizard
        - Open MiniTool, select your USB drive’s EFI partition, right click, select “Change Letter”, Click OK, Apply, OK
    - After that you can manage the EFI using Explorer++ in administrator mode
    - On macOS you can use Terminal to mount, or use EFI Mountain Snow.app to mount your USB EFI
    - If there is no EFI folder inside the EFI partition you need to create that first
 
Example Structure:
<p align=center>
    <img src="https://user-images.githubusercontent.com/33935034/150014815-9ff78610-aa98-45ad-9fe9-75b4d2c73886.png">
</p>

- After finished, next step is to boot the Installer USB
    - I suggest to boot with config_debug.plist because if anything will go wrong you’ll see the logs of what causing that. 
    - In Clover, select “Options” below the partitions, select “Configs”, then select “config_debug.plist” 
- Install macOS 
    - Don’t forget to boot from your USB after restarts 
        - If you install Monterey boot from Preboot only! 
- After installing you need to mount your USB’s EFI and your System Drive’s EFI then copy the CLOVER and BOOT folder to your System Drive’s EFI  
    - (again, if there is no EFI folder, you need to create it first) 
- Unmount and remove your USB Installer and restart your system 

## Post Installation
- Open up your config.plist with Clover Configurator.app, on SMBIOS tab, generate new SMBIOS, then you can log-in to iServices now
- Download <a href="https://github.com/zhen-zen/YogaSMC">YogaSMC.app</a> to manage your fan speed, charging threshold, other SMC related things

<p align=center>That’s it!</p>
<p align=center>Credit for <a href=https://github.com/tylernguyen>tylernguyen</a> for his hard work for creating SSDTs for Thunderbolt 3, he did an excellent job. Check out his work on the OpenCore side if you want</p>
<p align=center><b> Happy Hackintoshing!  </b></p>
<p align=center>2022</p>
<p align=center>Insanelymac - <a href="https://www.insanelymac.com/forum/profile/2210435-kushwavez/" target="_blank">@kushwavez</a></p>
<p align=center>GitHub - <a href="https://github.com/kushwavez" target="_blank">kushwavez</a></p>
<p align=center>Reddit - <a href="https://www.reddit.com/user/kushwavez" target="_blank">u/kushwavez</a></p>
<p align=center>Hungary 🇭🇺</p>
