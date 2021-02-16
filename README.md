#  Lenovo ThinkPad X1 Carbon 6th Gen [Big Sur 11 - Windows 10]
## Clover EFI for Lenovo ThinkPad X1 Carbon 6th Gen - macOS Big Sur
## Insanelymac: [[GUIDE] Lenovo ThinkPad X1 Carbon 6th Gen [Big Sur 11 - Windows 10]](https://www.insanelymac.com/forum/topic/346368-guide-lenovo-thinkpad-x1-carbon-6th-gen-big-sur-11-windows-10/)
<p align="center">
<img src="https://i.ibb.co/2FTNg5t/lenovo-x1-carbon-6th-20kh-png-45213fcfbc31a832fd51995162ddf9c3.png">
</p>
<p align="center"><b>Lenovo ThinkPad X1 Carbon 6th Gen</b></p>
<p align=center>macOS Install Instructions (Clover v5130)</p>
<p>For specs, notes, other informations see the linked Insanelymac guide</p>
<p align="center">
<img src="https://i.ibb.co/jv9SkRp/Screenshot-2021-02-14-at-20-24-31.png">
</p>

## Installation:
- Create a macOS USB Installer with any method you now.
    - For creating Big Sur Installer USB on Windows, use my guide: <a href="https://www.insanelymac.com/forum/topic/346703-guide-creating-clover-macos-big-sur-installer-usb-on-windows/" target="_blank">[GUIDE] Creating Clover macOS Big Sur Installer USB on Windows</a>
    - On macOS you can download the macOS Installer from App Store, or with <a href="https://github.com/corpnewt/gibMacOS" target="_blank">gibMacOS</a>, and create the USB Installer with the official <a href="https://support.apple.com/en-in/HT201372" target="_blank">"createinstallmedia"</a> method
    - For Sierra and older you need to use the official .dmg from Apple’s website.
- Mount your USB’s EFI and paste my CLOVER and BOOT folder from my bootpack
folder to it
    - On Windows you can mount your USB’s EFI with MiniTool Partition Wizard
        - Open MiniTool, select your USB drive’s EFI partition, right click, select “Change Letter”, Click OK, Apply, OK
    - After that you can manage the EFI using Explorer++ in administrator mode
    - On macOS you can use Terminal to mount, or use EFI Mountain Snow.app to mount your USB EFI
    - If there is no EFI folder inside the EFI partition you need to create that first
 
Example Structure:
<p align=center>
    <img src="https://i.ibb.co/5FZthw6/Picture-1.png">
</p>

- After finished, next step is to boot the Installer USB
    - I suggest to boot with config_debug.plist because if anything will go wrong you’ll see the logs of what causing that. 
    - In Clover, select “Options” below the partitions, select “Configs”, then select “config_debug.plist” 
- Install macOS 
    - Don’t forget to boot from your USB after restarts 
        - If you install Big Sur boot from Preboot only! 
- After installing you need to mount your USB’s EFI and your System Drive’s EFI then copy the CLOVER and BOOT folder to your System Drive’s EFI  
    - (again, if there is no EFI folder, you need to create it first) 
- Unmount and remove your USB Installer and restart your system 

## Post Installation
- Open up your config.plist with Clover Configurator.app, on SMBIOS tab, generate new SMBIOS, then you can log-in to iServices now
- Download <a href="https://github.com/zhen-zen/YogaSMC">YogaSMC.app</a> to manage your fan speed, charging threshold, other SMC related things

<p align=center>That’s it!</p>
<p align=center><b> Happy Hackintoshing!  </b></p>
<p align=center>2021</p>
<p align=center>Insanelymac - <a href="https://www.insanelymac.com/forum/profile/2210435-kushwavez/" target="_blank">@kushwavez</a></p>
<p align=center>GitHub - <a href="https://github.com/kushwavez" target="_blank">kushwavez</a></p>
<p align=center>Reddit - <a href="https://www.reddit.com/user/kushwavez" target="_blank">u/kushwavez</a></p>
<p align=center>Hungary 🇭🇺</p>
