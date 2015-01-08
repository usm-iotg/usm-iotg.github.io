---
layout: post
title: "Module 3: Galileo - Nodejs Server"
description: ""
category: Lessons
tags: [Galileo, Module-3]
---
{% include JB/setup %}

This written guide will introduce Node.js and to start development with Intel Galileo

# Node.js

Node.js is an open-source, cross platform runtime environment for server-side and networking application. Node.js application are written in JavaScript and can be run within the Node.js runtime on different platforms.

Here we list out some of the advantages of using Node.js:

* Provide rapid and robust development.
* Easy to build and scalable.
* There are a number of libraries to try on. 
* Real-time application fits quite well with Node.js
* Backed by wonderful and helpful community thus there are always answer out there.

and we think that there are some aspects that Node.js should not be used (maybe at least at this moment):

* Relational database tools are still not pleasant to work with. 
* **Heavy** server-side which involves **heavy** computation are not recommended.   

#### Node.js + Galileo: A good match?

Yup. Node.js actually enable Galileo for rapid development. Plus Node.js is easy to start. If you are looking at the Quark chip inside of Galileo (which powered by 400Mhz), it means that we need to have a not-so-heavy applications to run with. 

# Before You Start

* You will need Intel IoT XDK Edition to deploy, run and debug IoT application.
* You will need a working and stable internet connection. 
* an Micro-SD card.

*Note that in this guide, we use both Windows and Linux (Ubuntu 12.04) both for setting up the image to micro-SD, and run the project with Intel IoT XDK respectively. ([Intel IoT XDK](https://software.intel.com/en-us/html5/xdk-iot) are available on Linux, Windows and OSX)  

# 1. Prepare the Image

Download the latest image from IoT Devkit software [page](https://software.intel.com/en-us/iot/downloads). 

![](/img/devkit-download-page.png)

Direct link: [Intel Galileo Board(Linux Boot Image)](http://iotdk.intel.com/images/iot-devkit-latest-mmcblkp0.direct.bz2)

Extract the downloaded image using [7zip](http://www.7-zip.org/download.html).

![](/img/extract-devkit.png)

Download [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/) utility to write the image into Micro-SD card. Install it as an Administrator. After successful installation, run Win32DiskImager as an Administrator. 

Insert Micro-SD card and select the device drive for your inserted Micro-SD card. 

![](/img/win32diskimager.png)

Browse (Click on folder icon) and select the image. Be sure to select *.* file option in order to find your *.direct image. Then click **Open** to proceed. 

![](/img/win32diskimager-2.png)

Once everything is ready, write the image to selected Micro-SD card. 

![](/img/win32diskimager-3.png)

Upon completion, select **Exit** and close *win32diskimager* application. Now your micro-SD card is ready to be used with Galileo board. 

# 2. Boot the Image

Put Micro-SD card into SD slot in Galileo board and boot your image.

![](/img/insert-sd.png)

Power on Galileo board and let the booting process takes place. 

# 3. Attach Ethernet cable

Since we are using campus network, therefore we just attach Ethernet cable to Galileo while we will let Galileo to discover the IP (later on).

![](/img/connect-rj45.png)


## 4. Writing and Runing Simple HTTP Server with Nodejs

Now you have two options that you can choose:

* Use Intel IoT XDK or
* Clasically write up the code and run your HTTP server in terminal console

### 4.1 Using Intel IoT XDK

Open Intel IoT XDK application. From *Internet of Things (IoT) with Node.js Projects:*, click *"Start with a Sample or Template"*. Then, choose *"Analog Read"* template and then click *"Use This Template"*. 

![](/img/intel-iot-xdk.png)

Next, name your project as *http-server* and then click *Create* button to create the project.

![](/img/intel-iot-xdk-2.png)

You project will be created. You will see all the files created on left panel. Open *"main.js"* and remove all the sample codes and replace it with these lines:

![](/img/intel-iot-xdk-3.png)

<pre>
<code> 
var http = require("http");
var server = http.createServer(function(req, res){
	res.writeHead(200, "Content-Type" : "text/plain");
	res.end("hello world");
}).listen(5000);

console.log("Server is running http://X.X.X.X:5000");
</code>
</pre>

![](/img/intel-iot-xdk-4.png)

Open *package.json* file and replace *"AnalogRead"* with *"http-server"*.

![](/img/intel-iot-xdk-5.png)

Now connect to IoT device. Choose **"- Select a Device -"** and check either your IoT device is discovered. If not the you can click **"[%] Rescan for Devices"** to discover your IoT device. Once discovered, it should be displayed on the list with the IP address. 

![](/img/intel-iot-xdk-7.png)

To start connect, select your IoT device. Left **"Address: "** and **"Port: "** boxes as default. Tick **"Use secure connection"** and fill up **"User Name: "** with **root**.

![](/img/intel-iot-xdk-8.png) 

Click *Connect* to start connection and you may see as below upon successful connection. Take note on the IP address written. Now you can add the IP address in **console.log** by replacing **X.X.X.X.X** with the actual IP in your code (main.js).

<code>console.log("Server is running at http://10.207.146.57:5000");</code>

![](/img/intel-iot-xdk-10.png)

To build the project, click **Install/Build** icon as shown below and then click **Build** to proceed. 

![](/img/intel-iot-xdk-14.png)

Then upload the project to IoT device by clicking the **Upload** icon. 

![](/img/intel-iot-xdk-15.png)

After that, click **Run** to run your simple HTTP server. 

![](/img/intel-iot-xdk-16.png)

Simply check your running HTTP server. Open your browser and navigate to **"http://localhost:5000"**. You will see a "hello world" text.

![](/img/intel-iot-xdk-17.png)

