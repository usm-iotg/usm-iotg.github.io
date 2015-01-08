---
layout: post
title: "Module 1: Galileo - Get Started"
description: ""
category: Lessons
tags: [Galileo, Module-1]
---
{% include JB/setup %}

# Overview

Here we show you how to setup development environment for Intel Galileo in Windows. 

## Activity: Setup Galileo in Windows

This instruction is for the first time you setup Galileo in your PC. 

### 1. Download and install 7zip

Visit 7zip download page (choose the correct installer for your platform). Download and install in your machine.

![](/img/7zip.png)

### 2. Download Intel Galileo Software

Navigate to (Intel Galileo software)[] webpage. Download zip file for Windows. 

![](/img/galileo-software.png)

### 3. Extract

Extract downloaded zip file using 7zip. Make sure that you remember the path of extracted Galileo software. 

![](/img/galileo-software-extract-3.png)

### 4. Connect Galileo board

Attach power adapter to Galileo board and power it on. Insert micro-USB to "USB Client" port. Connect USB to your PC.

![](/img/connect-galileo.png)

### 5. Install Driver

Open "Device Manager". Once Galileo board is connected properly in your PC, you may find "Gadget Serial v2.4" in the list.

![](/img/device-manager.png)

To install the driver, right click at "Gadget Serial v2.4" and choose "Update Driver Software..."

![](/img/device-manager-2.png)

Choose "Browse for driver software on your computer"

![](/img/device-manager-3.png)

Select the path of the driver "C:/arduino-1.5.3-Intel.1.0.4\hardware\arduino\x86\tools" and click next.

![](/img/device-manager-4.png)

The path may vary therefore make sure that you know exactly the path of Galileo software that you had extracted. By default, Galileo driver is located here:
<pre>
<code>
..\arduino-1.5.3-Intel.1.0.4\hardware\arduino\x86\tools
</code>
</pre>

Galileo working port will appear upon successful driver installation. 

![](/img/device-manager-7.png)

### 6. Verify your Galileo Connectivity

Open "Device Manager" and make sure your Galileo port presents on the list.

![](/img/device-manager-8.png) 

Open Arduino IDE in your Galileo software directory.

![](/img/arduino-ide-directory.png)

Make sure to choose the correct Galileo board (Gen1 or Gen2) and also to choose the correct Galileo port. 

![](/img/verify-board-and-port.png)

### 7. Check Firmware Version

From Arduino IDE, navigate to *Help > Galileo Firmware Update*. Check current firware version displayed and make sure to upgrade to the latest Galileo version software shown from the message window.

![](/img/firmware-upgrade.png)

*info: It may take times to upgrade the firmware. Be careful not to miss-touch the cables during the time because this action may interrupt upgrading process. Sometimes upgrading process failed due to Galileo port changed. Verify the port (*Tools > Serial Port*) first and make sure that it appears in your Device Manager before starting firmware upgrade.*

### 8. Open Blink Example

Open Blink example (*File > Examples > 01.Basics > Blink*). Compile and Upload into Galileo.

![](/img/blink-example.png)

### 9. Compile 

![](/img/compile.png)

### 10. Upload

![](/img/upload.png)

### 11. Observation

The blink example simply blink a built-in LED (turn on and off the LED for 1 second cycle) during your observation. 

<iframe class="vine-embed" src="https://vine.co/v/OwXQe53ETB3/embed/postcard?audio=1" width="600" height="600" frameborder="0"></iframe><script async src="//platform.vine.co/static/scripts/embed.js" charset="utf-8"></script>



