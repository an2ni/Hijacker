# Hijacker

Hijacker is a Graphical User Interface for the penetration testing tools [Aircrack-ng, Airodump-ng](https://www.aircrack-ng.org/), [MDK3](https://tools.kali.org/wireless-attacks/mdk3) and [Reaver](https://tools.kali.org/wireless-attacks/reaver). It offers a simple and easy UI to use these tools without typing commands in a console and copy&pasting MAC addresses.

This application requires an **ARM** android device with an internal wireless adapter that supports **Monitor Mode**. A few android devices do, but none of them natively. This means that you will need a custom firmware. Any device that uses the BCM4339 chipset (MSM8974, such as Nexus 5, Xperia Z1/Z2, LG G2, LG G Flex, Samsung Galaxy Note 3) will work with [Nexmon](https://github.com/seemoo-lab/nexmon) (which also supports some other chipsets). Devices that use BCM4330 can use [bcmon](http://bcmon.blogspot.gr/).

An alternative would be to use an external adapter that supports monitor mode in Android with an OTG cable.

The required tools are included for armv7l and aarch64 devices as of version 1.1. The Nexmon driver and management utility for BCM4339 and BCM4358 are also included.

Root access is also necessary, as these tools need root to work.

## Features
### Information Gathering
* View a list of access points and stations (clients) around you (even hidden ones)
* View the activity of a specific network (by measuring beacons and data packets) and its clients
* Statistics about access points and stations
* See the manufacturer of a device (AP or station) from the OUI database
* See the signal power of devices and filter the ones that are closer to you
* Save captured packets in .cap file

### Attacks
* Deauthenticate all the clients of a network (either targeting each one (effective) or without specific target)
* Deauthenticate a specific client from the network it's connected
* MDK3 Beacon Flooding with custom options and SSID list
* MDK3 Authentication DoS for a specific network or to every nearby AP
* Capture a WPA handshake or gather IVs to crack a WEP network
* Reaver WPS cracking (pixie-dust attack using NetHunter chroot and external adapter)

### Other
* Leave the app running in the background, optionally with a notification
* Copy commands or MAC addresses to clipboard
* Includes the required tools, no need for manual installation
* Includes the nexmon driver and management utility for BCM4339/BCM4358 devices
* Set commands to enable and disable monitor mode automatically
* **Crack .cap files** with a custom wordlist
* Create **custom actions** and run them on an access point or a client easily
* Sort and filter Access Points and Stations with many parameters
* Export all gathered information to a file
* Add a persistent **alias** to a device (by MAC) for easier identification

<img src="https://github.com/chrisk44/Hijacker/raw/master/screenshots/airodump_view.png" width="256" hspace="2"><img src="https://github.com/chrisk44/Hijacker/raw/master/screenshots/mdk_view.png" width="256" hspace="2"><img src="https://github.com/chrisk44/Hijacker/raw/master/screenshots/reaver_view.png" width="256" hspace="2">

[More Screenshots](https://github.com/chrisk44/Hijacker/tree/master/screenshots)

## Installation
Make sure:
* you are on Android 5+
* you are rooted ([SuperSU](http://www.supersu.com/download) is required, if you are on CM/LineageOS install SuperSU)
* you have a firmware to support Monitor Mode on your wireless interface

#### Download the latest version [here](https://github.com/chrisk44/Hijacker/releases).

When you run Hijacker for the first time, you will be asked whether you want to install the nexmon firmware or go to home screen. If you have installed your firmware or use an external adapter, you can just go to the home screen. Otherwise, click 'Install Nexmon' and follow the instructions. After installing the firmware you will land on the home screen and airodump will start. Make sure you have enabled your WiFi and it's in monitor mode.

##### Note: On some devices, changing files in `/system` might trigger an Android security feature and your system partition will be restored when you reboot.

## Troubleshooting
This app is designed and tested for ARM devices. All the binaries included are compiled for that architecture and will not work on anything else. You can check whether your device is compatible by going to Settings: if you have the option to install Nexmon, then you are on the correct architecture, otherwise you will have to install all the tools manually ([busybox](https://play.google.com/store/apps/details?id=stericson.busybox&hl=el), aircrack-ng suite, mdk3, reaver, [wireless tools](https://hewlettpackard.github.io/wireless-tools/Tools.html), [libfakeioctl.so](https://github.com/seemoo-lab/nexmon/tree/master/utilities/libfakeioctl) library) and set the 'Prefix' option for the tools to preload the library they need.

In settings, there is an option to test the tools. If something fails, then you can click 'Copy test command' and select the tool that fails. This will copy a test command to your clipboard, which you can run in a root shell and see what's wrong. If all the tests pass and you still have a problem, feel free to open an issue here to fix it, or use the 'Send feedback' option in the app's settings.

If the app happens to crash, a new activity will start which will generate a bug report in your external storage and give you the option to send it by email. The report is shown in the activity so you can see exactly what will be sent.

#### Do not report bugs for devices that are not supported or when you are using an outdated version.

Keep in mind that Hijacker is just a GUI for these tools. The way it runs the tools is fairly simple, and if all the tests pass and you are in monitor mode, you should be getting the results you want. Also keep in mind that these are AUDITING tools. This means that they are used to TEST the integrity of your network, so there is a chance (and you should hope for it) that the attacks don't work on your network. It's not the app's fault, it's actually something to be happy about (given that this means that your network is safe). However, if an attack works when you type a command in a terminal, but not with the app, feel free to post here to resolve the issue. This app is still under development so bugs are to be expected.

## Warning
### Legal
It is highly illegal to use this application against networks for which you don't have permission. You can use it only on YOUR network or a network that you are authorized to. Using software that uses a network adapter in promiscuous mode may be considered illegal even without actively using it against someone, and don't think for a second it's untracable. I am not responsible for how you use this application and any damages you may cause.

### Device
The app gives you the option to install the nexmon firmware on your device. Even though the app performs a chipset check, mistakes happen. The app currently includes the Nexmon firmware for BCM4339 and BCM4358 *only*. Installing the wrong firmware on a device may damage it (and I mean hardware, not something that is fixable with factory reset). I am not responsible for any damage caused to your device by this software.

#### Consider yourself warned.

## Donate

If you like my work, you can buy me a beer. :)

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=VV5TEHL8S6UQ2)

