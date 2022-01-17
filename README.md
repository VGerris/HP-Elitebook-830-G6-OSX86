# HP Elitebook 830 G6 OSX86 (hackintosh)
OpenCore 0.7.7 and EFI folder 

This is based on two other projects on github that did not work out of the box for my HP 830 G6

OpenCore EFI for HP Elitebook 830-G6 with Montery(12.1)

## Basic Information

- Bios Version: latest as of 16-1-2021
- ME Firmware - disabled
- Intel i5-8365U with UHD 620
- 32 GB DDR4
- PNY 1TB NVMe SSD
- AX200 wifi / bluetooth

## What Works

- CPU and iGPU
- Speakers /  Headphones output
- Trackpad
- Joystick Mouse
- USB Ports (Including USB-C Port)
- LAN / Ethernet
- Fn keys
- Battery Status
- Wi-Fi / Bluetooth (MacBookPro15,2 as system for bluetooth works, MacBookAir8,2 not)
- HDMI output ( a bit buggy, not always )
- Sleep
- HDMI over USB-c ( tested Apple adapter )
- Dell D6000 dock with DisplayLink driver and 2 screens / audio

## To Fix

- Mic (ALC215 Not Supported even with latest AppleALC and Layout-ID 18 injected)
- Webcam ( might not be possible )

## Not tested

- Thunderbolt 3 - not visible in device properties but needs to be enables in BIOS for dock to work

## Won't Fix

- FingerPrint Sensor / TouchID (Not recognized)

## BIOS Settings

- You can enable Fastboot, VTd and VTx

- Disable Legacy boot and Secure boot

- iGPU Memory set to 64MB

- disable wake on LAN/USB whatever for sleep to work

## About Sleeping and Hibernation

Sleeping works well but you cannot enable hibernation. It will freeze up when macOS try to hibernate.

You can disable hibernation by follow steps:

```bash
sudo pmset -a hibernatemode 0
sudo rm /var/vm/sleepimage
sudo mkdir /var/vm/sleepimage
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```

## About this project 

Limited support - make sure to use your own DSDT dump and troubleshoot
The EFI worke for me after an upgrade from Catalina - it might not work with the installer, but it should
Make sure to fill in your own serial, follow the Dortania guide:
https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios (choose model MacBookPro15,2)

Thanks to:
https://github.com/stevedat/HP-Elitebook-830-G6-Hackintosh
snd
https://github.com/tookdes/HP-Elitebook-830-G6-Hackintosh
and all the great people making this possible!

P.S. If you know how to fix the mic or webcam, please make a PR or a ticket.
Thank you 



