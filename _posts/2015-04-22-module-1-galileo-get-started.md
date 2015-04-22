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

### 1. Download Intel Galileo Software

Navigate to [Intel Galileo software](https://downloadcenter.intel.com/download/24355/Intel-Galileo-Software-Package-1-0-4) download webpage. Choose a correct software package accordingly to your platform (The current version of Galileo software at the time of writing is 1.0.4). 

![](/img/module-1_galileo-software-download-webpage.png)

For Windows, you can download "IntelArduino-1.6.0-Windows-Installer.exe" software package to eliminate the hussle of manual installation.

![](/img/module-1_galileo-software-windows-exe.png) 

### 3. Install the software

Run the self-extractor package (.exe file) to install Galileo software. 

![](/img/module-1_galileo-software-exe.png)

### 4. Connect Galileo board

Attach power adapter to Galileo board and power it on. Insert micro-USB to "USB Client" port. Connect USB to your PC.

![](/img/connect-galileo.png)

### 5. Verify your Galileo Connectivity

Open "Device Manager" and make sure your Galileo port presented on the list in 'Ports (COM & LPT)'.

![](/img/module-1_device-manager.png) 

### 6. Open Arduino IDE 

Open Arduino IDE (current version of Arduino IDE is 1.6.0).

![](/img/module-1_arduino-ide-1.6.0.png)

Make sure to choose the correct Galileo board (Gen1 or Gen2) and also to choose the correct Galileo port. 

![](/img/module-1_arduino-ide-1.6.0-select-board.png)

![](/img/module-1_arduino-ide-1.6.0-select-port.png)

### 8. Open Blink Example

Open Blink example (*File > Examples > 01.Basics > Blink*). Compile and Upload into Galileo.

![](/img/module-1_arduino-ide-1.6.0-blink-example.png)

### 9. Compile 

![](/img/module-1_arduino-ide-1.6.0-blink-compile.png)

### 10. Upload

![](/img/module-1_arduino-ide-1.6.0-blink-upload.png)

### 11. Observation

The blink example is a kind a 'hello world' in embedded world. This code sample simply blinks a built-in LED (turn on and off the LED for 1 second cycle). What is the idea behind blink example? Could you think of it?

<iframe class="vine-embed" src="https://vine.co/v/OwXQe53ETB3/embed/postcard?audio=1" width="600" height="600" frameborder="0"></iframe><script async src="//platform.vine.co/static/scripts/embed.js" charset="utf-8"></script>