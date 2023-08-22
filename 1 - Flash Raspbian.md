# 1 - FLASH RASPBIAN: Set up headless Raspbian Lite

## Table of contents

- [ ] [Summary](1%20-%20Flash%20Raspbian.md#summary)
- [ ] [Flash Raspbian onto SD Card](1%20-%20Flash%20Raspbian.md#flash-raspbian-onto-sd-card)
- [ ] [Set up Wi-Fi and SSH (THESE STEPS ARE NOT NECESSARY IF YOU USED THE RASPBERRY PI IMAGER)](1%20-%20Flash%20Raspbian.md#set-up-wi-fi-and-ssh-these-steps-are-not-necessary-if-you-used-the-raspberry-pi-imager)
- [ ] [Boot up the Raspberry Pi](1%20-%20Flash%20Raspbian.md#boot-up-the-raspberry-pi)
- [ ] [Next Steps](1%20-%20Flash%20Raspbian.md#next-steps)

## Summary

The **first step** to **start your project** is to **flash an OS into your Raspberry Pi**.
There are many available, but the best Linux-based system that was tailored to the Pi is **Raspbian**.
**Raspbian** comes in 2 flavors, **full**, or **lite**. **Full** comes with a **GUI**, allowing you to plug your Pi into a monitor, keyboard and mouse, and use it as a **traditional computer**. **Lite**, on the other hand, interfaces only with a **UNIX terminal**. You can still plug in a monitor and a keyboard, but the terminal is the only way to interface with the Pi. If you don't plan to use the Pi in a user-friendly way, or you don't plan to have it accessible with a setup station (monitor + keyboard + mouse), then the best idea is to flash the **lite version of Raspbian** and **access the Pi remotely**.

## Flash Raspbian onto SD Card

- [ ] **Get a Micro SD card**.
  > [!NOTE]
  > *Anything 8Gb or over will do, this will also be how much space you end up with in the Pi once it is running.*
  
- [ ] **Plug it into a computer of your choice**.
  > [!NOTE]
  >
  > - *If you don't plan on using the Raspberry Pi imager, you will need a computer with a UNIX terminal (Linux-based will work, MacBooks have UNIX terminals).*
  > - *If your computer has Windows installed, you can [install WLS](https://learn.microsoft.com/en-us/windows/wsl/install) to get a UNIX-based terminal directly into your terminal window.*

- [ ] **Download the Raspberry [Pi Imager tool](https://www.raspberrypi.com/software/)**, and open it.
  > [!WARNING]
  > **DO NOT USE ANOTHER IMAGER**. If you plan to **fully connect to the Pi remotely** (completely headless installation), and you don't have a monitor or don't want to set up a whole system only for your project, you are going to **need to set up SSH**. SSH is a way to connect to the Raspberry Pi's terminal directly from yours as if you were typing directly into it. Traditionally, you could connect to a fresh installation of Raspbian using the default user and password "pi" and "raspberry", but recently, due to security concerns, these **will not work until you have set up at least one user at the Pi**. This means that if you use another imager to flash the OS image into the SD card, **you will have to set up a monitor and keyboard at least once**, to set up a user, so you can access the Pi remotely in the future. This can be **prevented by using the RPi imager**, which **allows you to specify a user, and SSH settings while burning the image**.

- [ ] **Choose `Raspberry Pi OS Lite (64 bit)`**.

- [ ] **Choose your media (Micro SD)**.

- [ ] On the cog icon, **enter the settings BEFORE YOU FLASH**.

  - [ ] Under `Configure wireless LAN`, **set up your network's `SSID` and `Password` of whichever network you want the Pi to connect to**.

  > [!NOTE]
  > *Keep in mind Raspberry Pis do **not** support 5Gh band access points.*

  - [ ] **Change your `Wireless LAN country`** to your **country code** (US).

  - [ ] **`Enable SSH`** and **`Set username and password`**. Fill in the settings **`Username`** and **`Password`** as you will need them to connect to it later.

  - [ ] **Activate `Set locale settings`** and enter the corresponding settings for your locale.

  > [!NOTE]
  > *You might want to change the Pi's `hostname` to something recognizable, to be able to find it easier in your network.*

- [ ] **Save the settings, and click on `WRITE`**.

## Set up Wi-Fi and SSH (THESE STEPS ARE NOT NECESSARY IF YOU USED THE RASPBERRY PI IMAGER)

> [!WARNING]
> **These steps are not necessary if you used the Raspberry Pi imager.**

- [ ] In a UNIX based terminal, **navigate to the SD card's root directory**.
  > [!NOTE]
  > Use the `ls` command to list files and directories within your working directory, and the `cd` command to change your working directory.

- [ ] You need to **create a file called `wpa_supplicant.conf`** that contains the network settings. You can use the `nano` text editor for this. It comes standard in most Linux distributions, but if not you can install it.
  - [ ] To install `nano`, run: `sudo apt-get install nano`

- [ ] To create the file, run: `nano wpa_supplicant.conf`

- [ ] In the `nano` text editor, **paste this**:

```bash
country=us
update_config=1
ctrl_interface=/var/run/wpa_supplicant

network={
 scan_ssid=1
 ssid="MyNetworkSSID"
 psk="Pa55w0rd1234"
}
```

- [ ] **Replace your country** by your country code.

- [ ] **Replace the `SSID` and `psk`** with your access point name and password. The name and password should be surrounded by quotes `""`.

- [ ] **`Ctrl + O` and then `Enter` to save, and `Ctrl + X` to close**.

- [ ] Now, we need to **create an empty file called `ssh`** to let Raspbian know we want to enable `ssh` functionality.

  - [ ] In the SD card directory, run: `touch ssh`. **This creates an empty ssh file**.

## Boot up the Raspberry Pi

- [ ] Take the SD Card out of your computer and **insert it into the Pi**.

- [ ] The Pi will **install Raspbian**, **boot up**, and **connect to your network with an SSH connection open**.

## Next Steps

- Learn how to set up remote access to your Pi.

  - Go to [2 - Connect through SSH](2%20-%20Connect%20Through%20SSH.md)
  
- [Back to README](README.md)
