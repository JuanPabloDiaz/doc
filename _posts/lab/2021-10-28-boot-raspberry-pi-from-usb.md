---
layout: post
title: "How to Boot Raspberry Pi 4 From a USB SSD HDD"
date: 2021-10-28
categories: home-lab
tags: home-lab neverstoplearning raspberrypi
---

A Raspberry Pi is such a useful device so why don't give it more power by making it boot from an SSD instead of the default SD card?
Raspberry Pi Desktop is the recommended OS for this tutorial. Visit the link to learn how to [Setting up your Raspberry Pi](https://www.raspberrypi.com/documentation/computers/getting-started.html)

1.  Connect to Raspberry Pi over SSH
    Default username is pi & password is: raspberry

    ```bash
    ssh pi@YOUR_RPI_IP
    ```

2.  Update OS and firmware

    ```bash
    sudo apt update && sudo apt full-upgrade
    sudo rpi-update
    ```

3.  Reboot Raspberry Pi

    ```bash
    sudo reboot
    ```

4.  How to Update EEPROM on Raspberry Pi 4 For USB Boot...

    Install latest bootloader

    ```bash
    sudo rpi-eeprom-update -d -a
    ```

5.  Launch this tool for final configurations

    ```bash
    sudo raspi-config
    	advance options > boot order > USB
    	advance options > bootloader Version > E1 - last version ROM
    	display options > Resolution > MODE 82 - 16:9
    ```

6.  Reboot Raspberry Pi

    ```bash
    sudo reboot
    ```

7.  Copy SD to USB or SSD

    1. Connect to Pi using HDMI or VNC
       - **Enable VNC in the Pi**
         Interface menu > VNC > enable. Using the code below:
         ```
         sudo raspi-config
         ```
    2. Go to Menu > accessories > SD card copy.
    3. From SD (dev/mmcblk) to SSD

    ```bash
    sudo reboot
    ```

8.  Once it Finish, Turn off the pi

        remove the SD and boot from SSD

        ```bash
        sudo poweroff
        ```

    <br>

---

This article is publish in [Dev](https://dev.to/1diazdev/how-to-boot-raspberry-pi-4-from-a-usb-ssd-hdd-5ffa)
