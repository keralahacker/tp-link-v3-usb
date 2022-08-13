## TP-Link TL-WN722N v2/v3

# Realtek rtl8188eus &amp; rtl8188eu &amp; rtl8188etv WiFi drivers
### rtl8188eus v5.3.9 
[![Monitor mode](https://img.shields.io/badge/monitor%20mode-supported-brightgreen.svg)](#)
[![Frame Injection](https://img.shields.io/badge/frame%20injection-supported-brightgreen.svg)](#)
[![MESH Mode](https://img.shields.io/badge/mesh%20mode-supported-brightgreen.svg)](#)
[![GitHub issues](https://img.shields.io/github/issues/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/issues)
[![GitHub forks](https://img.shields.io/github/forks/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/network)
[![GitHub stars](https://img.shields.io/github/stars/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/stargazers)
[![GitHub license](https://img.shields.io/github/license/aircrack-ng/rtl8812au.svg)](https://github.com/aircrack-ng/rtl8188eus/blob/master/LICENSE)<br>
[![Android](https://img.shields.io/badge/android%20(8)-supported-brightgreen.svg)](#)
[![aircrack-ng](https://img.shields.io/badge/aircrack--ng-supported-blue.svg)](#)


# Supports
* Android 7
* MESH Support
* Monitor mode
* Frame injection
* Up to kernel v5.8+
... And a bunch of various wifi chipsets

TP-Link TL-WN722N v2/v3 [Realtek RTL8188EUS], you might find this helpful. In the begining, I am able to enter monitor mode. However after a few days, I found out it doesn't allow to enter monitor mode. I think  TP-Link TL-WN722N v2/v3 have automatically updated its driver. Then

1. sudo apt update
2. sudo apt upgrade 
3. sudo apt-get dist-upgrade
4. reboot
5. sudo apt-get install linux-headers-$(uname -r)
6. sudo apt install bc 
7. sudo apt-get install build-essential
8. sudo apt-get install libelf-dev
10. sudo apt install dkms
11. sudo rmmod r8188eu.ko 
12. git clone https://github.com/keralahacker/tp-link-v3-usb
13. cd tp-link-v3-usb
14. sudo -i
15. echo 'blacklist r8188eu'|sudo tee -a '/etc/modprobe.d/realtek.conf'
16. reboot
17. cd tp-link-v3-usb 
18. sudo unzip rtl8188eus-tplink-v3-2022-08.zip
19. cd rtl8188eus-tplink-v3-2022-08
20. sudo make && make install
21. reboot 

Like https://github.com/cccooo/rtl8812au-centos-7.6, forked from aircrack-ng/rtl8188eus and modified for CentOS 7.9
as CentOS Kernel 3.10 contains many code from 4.x


# Howto build/install
1. You will need to blacklist another driver in order to use this one.
2. `echo 'blacklist r8188eu'|sudo tee -a '/etc/modprobe.d/realtek.conf'`
3. Reboot
4. cd rtl8188eus
5. `make && sudo make install`
6. Reboot in order to blacklist and load the new driver/module.

# MONITOR MODE howto
Use these steps to enter monitor mode.
```
$ sudo airmon-ng check kill
$ sudo airmon-ng start <interface>

```
Frame injection test may be performed with
(after kernel v5.2 scanning is slow, run a scan or simply an airodump-ng first!)
```
$ aireplay -9 <interface>
```


# Credits
Realtek       - https://www.realtek.com<br>
Alfa Networks - https://www.alfa.com.tw<br>
aircrack-ng.  - https://www.aircrack-ng.org<br>
<br>
And all those who may be using or contributing to it of anykind. Thanks!<br>

----------------------------------------------------------------------------------
#### if you face any issues ===> 
https://github.com/keralahacker/tp-link-v3-usb/issues/new 
#### submit with screenshot
----------------------------------------------------------------------------------


### Deauthentication Attack[for educational purpose only]



airodump-ng wlan0

airodump-ng --bssid <id> --channel <ch> --write test wlan0

aireplay-ng --deauth [any no.] -a <bssid> -c <station id> wlan0


## Important note: 

If after restarting your kali machine doesn't recognise your device..
As lot of people are facing the same problem ..
I have a solution for you..
Whenever you restart your kali OS
Insert the adapter and run the command


sudo rmmod r8188eu.ko

sudo modprobe 8188eu

Disconnect the device and connect again..
