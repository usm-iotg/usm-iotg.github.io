---
layout: post
title: "Module 5: Yocto Image (Part 4) - Explore Yocto"
description: ""
category: Lessons
tags: [Galileo, Module-5]
---
{% include JB/setup %}

Build a Yocto image might take times to complete but once you have succesfully bake the image, it is time to explore on what can you do with the image. Here we list-out a few things that you can do to start your hacking. 

## 1. How to access command-line terminal

To be able to access command-line terminal is crucial. Therefore here we list out a few options on how you can access command-line terminal inside Galileo. 

### 1.1 Serial Console

#### 1.1.1 Intel Galileo (Gen 1)

Galileo Gen1 provides terminal interface UART 3.5mm jack RS232 port over USB, requires special cables as you need to have a pair of USB-to-RS232 cable and RS232-to-3.5mm jack.

![](/img/3.5mm-rs232-usb.png) 

Connect at terminal interface 3.5mm jack on Intel Galileo (Gen1).

![](/img/connect-uart-2.png)

#### 1.1.2 Intel Galileo Gen 2

In second generation of Intel Galileo requires FTDI cables (USB to Serial) TTL 3.3v Level. You can buy FTDI cable online with [Mouser Electronics](http://my.mouser.com/ProductDetail/FTDI/TTL-232R-3V3/?qs=Xb8IjHhkxj627GFcejHp0Q==).

![](/img/ftdi-cable.png)

Attach FTDI cable through 6-pin connector on Intel Galileo Gen2. 

![](/img/connect-ftdi.png)

Check Galileo port. For Linux user, you might want to enable the serial port. 

![](/img/galileo-serial-port-2.png)

Start serial console connection with PuTTY. Download [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe) and do the following settings:

##### *Windows

Make sure that you use the correct COM for connection. Set the speed to 115200. 

![](/img/putty-setting.png)

In Terminal -> Keyboard, set "The function keys and keypad" to "SCO" then click "Open" to start. 

![](/img/putty-setting-2.png)

##### *Linux (Ubuntu 12.04)

You may use Minicom or PuTTY to connect to serial console. 

![](/img/minicom.png)

Upon successfull connection, you may see the console login screen. Use "root" to access. 

![](/img/root.png)

## 2. Command Utilities

Here we listed some important command-line tools which people might use it almost all the time. 

### 2.1. Netstat

Netstat(network statistic) is used to display active TCP connection and details on each individual connection.

<code>$ netstat ntap </code>

![](/img/netstat.png) 

### 2.2 ifconfig/ifup

Both ifconfig and ifup are used to activate network interfaces. On the other perspective, *ifconfig* directly control network interfaces while *ifup* executes some scripts(ifup-scripts and ifdown-script). An 

<code>$ ifconfig eth0 up </code>

activates *eth0* but does not setup IP address, 

![](/img/ifconfig.png)

However an 

<code>$ ifup eth0 </code>

setup IP address or other options based by an ifcfg-eth0. 

![](/img/ifup.png)

Remember to connect network cable to Ethernet port at Galileo board. 

![](/img/connect-rj45.png)

## 3. SSH

When your Galileo board has an IP address and SSH-enabled connection, you can access your Galileo remotely via ssh. Example:

<code> $ ssh root@10.207.146.57</code>

![](/img/ssh-4.png)

## 4. Top

Top command is a system monitoring tool. By default, *top* command displays the processes in the order of CPU usage. Enter "*top*" in terminal to start using *top*.

<code>$ top</code>

![](/img/top.png)

## 5. Check Galileo Firmware Version

You can use *cat* command to display current version of firmware of Galileo. Please update the firmware if current firmware is out-dated. 

<code>$ cat /etc/sysfirmware/board_data/flash_version</code>

![](/img/cat.png)

## 6. Set Time/Date

Use *date* command to display and set system's date and time. By default, the format to set is MMDDhhmmYYYY. Example:

<code>$ date 121714002014 </code>

![](/img/set-date-time.png)

will set the date to *Dec 17 14:00:00 UTC 2014*. Please remind that rebooting action will reset the date and time. 