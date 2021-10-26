# BuddyTablet a Raspberry Pi 4 Tablet With No Soldering

The goals of the BuddyTablet are as follows:
- Linux based OS
- 1 TB of storage plenty of room for media, photos, games, and applications
- External ports for power, video, and USB
- At least one hour of battery life, and must be direct pluggable into the wall
- Should be capable of software development Go, Python3, Docker
- Blue Tooth audio support
- External display support, portable monitors (https://youtu.be/YAZuRCUISaE) or desktop monitors
- Must be able to watch videos YouTube, NetFlix, Hulu, HBO Max, Apple TV, etc
- No soldering

[Images of the BuddyTablet are here](https://github.com/rovitotv/BuddyTablet/tree/main/Images)

# Hardware

## Parts List

| Part Name                       | Link                                                                                                | Cost (USD) |
|:--------------------------------|:----------------------------------------------------------------------------------------------------|:-----------|
| Battery PiSugar 2 Pro           | https://www.amazon.com/Pisugar2-Portable-Platform-Raspberry-Accessories/dp/B08D8PPCKN               | 49.99      |
| Raspberry Pi 7" touch screen    | https://www.amazon.com/Raspberry-Pi-7-Touchscreen-Display/dp/B0153R2A9I                             | 89.99      |
| 3M screws for case and SSD      | https://www.amazon.com/VIGRUE-570PCS-Stainless-Assortment-Machine/dp/B08H24W42K                     | 14.44      |
| 2.5M standoffs for raspberry pi | https://www.amazon.com/Sutemribor-Female-Spacer-Standoff-Assortment/dp/B075K3QBMX                   | 12.99      |
| Kingston A400 960 GB SSD        | https://www.amazon.com/Kingston-960GB-Solid-SA400S37-960G/dp/B079XC5PVV                             | 84.99      |
| Raspberry Pi 4 8 GB model       | https://www.pishop.us/product/raspberry-pi-4-model-b-8gb/?src=raspberrypi                           | 75.00      |
| Fan with Large heat sync        | https://www.amazon.com/GeeekPi-Raspberry-Low-Profile-Cooling-Heatsink/dp/B07ZV1LLWK/                | 19.99      |
| SATA to USB cable               | https://www.amazon.com/StarTech-com-10Gbps-Adapter-Cable-Drives/dp/B00XLAZODE                       | 18.83      |
| USB 3.0 cables L shaped         | https://www.amazon.com/gp/product/B07F7Y21GW                                                        | 11.99      |
| Power Supply                    | https://www.amazon.com/dp/B07TSFYXBC                                                                | 10.99      |
| Total                           |                                                                                                     | 389.20     |

A total of 389.20 sounds like a lot of cash but if you consider a iPad with 256 GB of storage and WiFi only is 479 you are saving ~ 100.  Try and get a
iPad with 1 TB and you have to select the iPad Pro and the cost is 1,499 for a savings of 1,110!

You could save money by reducing storage or reducing the amount of RAM on the Raspberry Pi 4, the BuddyTablet can be customized to meet your needs.

## Benchmarks for SSD/NVMe on Raspberry Pi

https://jamesachambers.com/2020s-fastest-raspberry-pi-4-storage-sd-ssd-benchmarks/

Is a USB flash drive worth trying? https://www.amazon.com/PNY-Elite-Flash-Speeds-P-FD1TBPRO-GE/dp/B01E17LOL6?tag=w050b-20&th=1
Pi benchmarks on the PNY: https://pibenchmarks.com/brand/PNY_Pro_Elite_USB

## 2.5" SSD specifications

https://www.snia.org/technology-communities/sff/specifications?field_doc_status_value=All&combine=8201&items_per_page=20


## Future version with higher resolution screen

- Reviewed on YouTube: https://youtu.be/5Ffu75vIExA
- 7" screen: https://www.amazon.com/WIMAXIT-Raspberry-Monitor-1024x600-Raspbian/dp/B0932CX42D?dchild=1&keywords=raspberry+pi+4+touch+screen,wimaxit+7+inch+portable&qid=1632764122&sr=8-4&linkCode=sl1&tag=leepspvideous-20&linkId=16a5692dae5cdce19ec18e9fef60c00d&language=en_US&ref_=as_li_ss_tl
- 14" screen: https://www.amazon.com/gp/product/B08JLWNX22?pf_rd_r=6TZTJEVNCV2MCZWQPM9Z&pf_rd_p=edaba0ee-c2fe-4124-9f5d-b31d6b1bfbee&linkCode=sl1&tag=leepspvideous-20&linkId=463d5c30053121edecd54bc44dc5ede7&language=en_US&ref_=as_li_ss_tl

## PiSugar 2 Pro Battery

The battery on the PiSugar 2 Pro is 5,000 mAH which is large!  Modern smart phones are usually less than 4,000 mAH. 
Try and keep your expectations in check usually I see 1.5 hours - 2 hours of battery life.  Recall we are powering a
screen, SSD, and fan.  By reducing the brightness of the screen and turning down the CPU frequency can extend battery
life.  If you need more power you can always plug in a external battery pack to carry you along for more time on the
BuddyTab.

### Useful Links on the PiSugar 2 Pro Battery

- [James Chambers Blog post about the PiSugar 2 Pro Battery](https://jamesachambers.com/ups-backup-battery-for-raspberry-pi-pisugar-solderless-setup/)
- [ETA Prime YouTube review of the PiSugar 2 Pro Battery](https://youtu.be/UlirpA-6tCQ)
- [ETA Prime YouTube review of the PiSugar S Plus](https://youtu.be/HUL5Ii0dD7E) you could save yourself 20 dollars by using this model but you lose the web gui.
- [Comparison table at the bottom of the different battery systems PiSugar offers](https://www.tindie.com/products/pisugar/pisugar-s-plus-battery-for-raspberry-pi-3b3b4b/)

### 3D case model

- we tried to use the panel but lining it up was a pain, maybe in version 2?

https://github.com/PiSugar/PiSugar/tree/master/model_pro



# Raspberry Pi OS Setup

We are going to use 32 bit of Raspberry Pi OS to make sure we can hardware accelerated
Chrome and VLC.  To start we are going to use Raspberry Pi OS to keep things simple with
no special programming required.  

## Creating new user for your BuddyTablet

I recommend that you create a user other than the default user of pi.  
[Follow the Raspberry Pi OS directions here](https://www.raspberrypi.com/documentation/computers/using_linux.html#creating-a-new-user) to 
create another user. To change the default user on a new boot [read this post](https://forums.raspberrypi.com/viewtopic.php?t=310024). 
Other steps you should take is add the newuser to a few useful groups with the following commands:

```bash
sudo adduser new_user_name bluetooth
sudo adduser new_user_name netdev
```

## How to Run Programs Without Warning

Open PCManFM, Go to Edit/Preferences/General, Check box for "Don't ask options on launch executable file".
This tip came from [Unix Stack Exchange](https://unix.stackexchange.com/questions/487504/lxde-desktop-shortcut-remove-prompt-that-ask-action-open-execute).

## Matchbox on-screen keyboard

Install the matchbox on-screen keyboard with this command:
```bash
sudo apt install matchbox-keyboard
```

## Add Icons to Desktop

- Find application in the "Raspberry Pi Menu"
- Right click application, then select add to desktop

A ".desktop" file will be created, icons I have made include:
- CommanderPi
- Chromium Web Browser
- Terminal
- Keyboard
- Calculator
- File Manager

## PiSugar2 Battery Management Software

The software is described here on [github](https://github.com/PiSugar/pisugar-power-manager-rs).  Install
with this command:

```bash
curl http://cdn.pisugar.com/release/pisugar-power-manager.sh | sudo bash
```

After the software is installed you can check battery life in web browser with this URL:
[battery management](http://192.168.1.153:8421/#/)

## CommanderPi

CommanderPi lets you overclock the CPU/GPU easily and shows temperate and other real time
statistics. To learn more about CommanderPi including how to install the software
check out [CommanderPi's GitHub](https://github.com/Jack477/CommanderPi).

## RPI Backlight

[RPI Backlight](https://github.com/linusg/rpi-backlight) allows a user to set the backlight
of the display.  Recall we have no ambient light sensor so the display needs to be set on
its own by the user.  [Follow the directions](https://github.com/linusg/rpi-backlight) to
install the software.  We highly recommend [following the directions here](https://rpi-backlight.readthedocs.io/en/latest/usage.html#adding-a-shortcut-to-the-lxde-panel)
in order to install rpi-backlight-gui in the menu bar.  

## Bluetooth

The bluetooth application that comes with Raspberry Pi OS doesn't work very well, so
I recommend blueman-applet.  You can install blueman-applet with these commands:

```bash
sudo apt update
sudo apt upgrade
sudo apt install bluetooth pi-bluetooth bluez blueman
```

[To learn more about blueman-applet read this blog post.](https://pimylifeup.com/raspberry-pi-bluetooth/) 

## Netflix, Disney+, Hulu, HBO Max, video playback

The Raspberry Pi OS doesn't ship with Widevine digital rights management (DRM) content
protection which all the major streaming services use to protect their content. But 
Widevine is available to the Raspberry Pi OS and can be installed with these simple
commands:

```bash
sudo apt update
sudo apt upgrade
sudo apt install libwidevinecdm0
```

After installing the libwidevine package simply restart Chromimum and you will then
be able to watch your favorite streaming service.  [To learn more about installing Widevine DRM 
read this blog post.](https://pimylifeup.com/raspberry-pi-widevine/).

## Games

[Maelstrom](https://en.wikipedia.org/wiki/Maelstrom_(1992_video_game)) a asteroids clone from the 1990's and ported to Linux:

```bash
sudo apt-get install maelstrom
```


# 3D Printing

All the parts were printed with PLA using a Creality Ender 3V2 3D printer. Blender was
used to create the 3D models to create the BuddyTablet.  The blender file is BuddyTab.blend.
Blender is open source software and is supported on Linux, Mac OS X, and Windows. 

## Measurements

- M2.5 screw holes should be 2.75 mm in diameter
- M3 screw holes should be 3.25 mm in diameter

- screw_hole_front: -4.7416, 79.258, 11.95
- screw_hole_back: -4.7416, 2.6281, 11.95
- standoff_1: -37.739, 73.48, 22
- standoff_0:  10.063, 73.48, 22

- screen_rail_top: 2.4884, 0, 113.33; rotation 0, -20, 0; dim 2, 163, 10
- screen_rail_bottom: 23.949, 0, 50.577; rotation 0, -20, 0; dim 2, 163, 10

- right clip: -36.025, -86.34, 130.86 move z +2 mm 132.86
- left clip: -36.025, 85.82, 130.86 move z +2 mm 132.86
- back: -41.845, 0, 78.856 dim: 2, 164, 110
- back bottom: -42.1, 0, 15.55 dim 2, 190, 17
- base bottom: -5.1179, 0, 7.8904 dim 72, 190, 2
- base top: -7.5864, 73.684, 23.041 scale: 32.5, 2.5, 1 dim: 72, 190, 2

- port panel: 73.415, 87.505, 7.0772 dim: 60, 17, 5.2

- external USB ports 1.5 cm x 1 cm or 15 mm x 10 mm

- right bracket -5.1305, 75.466, 24.869 scale: 35, 6, 1 Dim: 70, 12, 2

# Advanced OS setup

This section is experimental and not completed.

## How to Build QT 5.15 LTS

https://www.tal.org/tutorials/building-qt-515-raspberry-pi

## How to Build KDE Plasma Mobile

https://community.kde.org/Get_Involved/development#Set_up_kdesrc-build



