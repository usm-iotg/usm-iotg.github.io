---
layout: post
title: "Module 1: Basics on Arduino IDE"
description: ""
category: Lessons
tags: [Galileo, Module-1]
---
{% include JB/setup %}

In this guide, we will discuss some basics on Arduino IDE and Arduino sketch programming.

# Arduino IDE for Intel Galileo

Arduino IDE is a cross-platform (available in Linux, Windows and OSX) used to write a code for Arduino boards. It is written in Java and is based on Processing programming and Wiring project. In Arduino world, the code written is called a **"sketch"**. Arduino IDE has it own version for supporting Intel Galileo (current version as this written guide is version [1.0.4](https://communities.intel.com/docs/DOC-22226)). 

# Basics

This is how the Arduino IDE for Intel Galileo should looks like. As you may realize that the word **"Intel"** and the version of Galileo software should differentiate between default Arduino IDE and Arduino IDE for Intel I/O boards. 

![](/img/arduino-ide-anatomy.png)

Here are some of the basics that you should know:

### Verify Board Connectivity before Uploading

##### Choose I/O board

Make sure that you connect to the correct Intel I/O board. Click **Tools** > **Board** > *your Intel board*.

![](/img/arduino-ide-anatomy-6.png)

##### Check Port

Ensure that you connect to the correct port. Port may appears differently according to the platform you use. (For Windows, you might see COM1, COM2 or etc, check Windows *Device Manager*; In Linux you may notice /dev/ttyACM0;)

![](/img/arduino-ide-anatomy-7.png)

### Compile & Upload 

![](/img/arduino-ide-anatomy-5.png)

### Serial Monitor

Serial monitor allows data to be displayed from the I/O board. Use **Serial** API to enable communication between built-in serial monitor with the board. Click the serial monitor button in the toolbar and select the same baud rate used in the call to *begin()*.

![](/img/arduino-ide-serial.png)

### Firmware Upgrade

***Always make sure that you have select the I/O board and port. Otherwise the upgrade process will not work*. 

Click **Help** > **Galileo Firmware Upgrade** to check and upgrade the firmware of Galileo board. It may takes a few minutes for upgrading process to complete. We recommend you to check the current version of firmware and upgrade it when necessary. Please make sure that you have the latest firmware version within your I/O board. 

![](/img/firmware-upgrade.png)

##### process flow

![](/img/firmware-upgrade-2.png)

If the firmware upgrade stuck for more than 10 minutes, or you got any upgrade error:

* unplug cables.
* retry the firmware upgrade procedure again. 