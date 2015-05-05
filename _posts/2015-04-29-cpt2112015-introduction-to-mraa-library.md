---
layout: post
title: "CPT211/2015: Introduction to MRAA library"
description: ""
category: Lessons
tags: [Galileo, CPT211]
---
{% include JB/setup %}

info: This tutorial is written for CPT211 Programming Languages Concepts and Paradigms of semester 2 academic session 2014/2015.

## Overview

MRAA library is a low level skeleton C/C++ library with bindings to javascript & python, providing interface with the IO on Galileo, Edison and other platforms. 'libmraa' does not ties developer to a specific platforms but supports across different platforms with generated portable code. Furthermore, mapping sensors and actuators on top of the supported hardware and platforms give an ease for developers and makers which allow control of low level communication protocol by high level languages and constructs. 

## Simple Analog Temperature Sensor with 'libmraa'

Try out this code and see how it works. Make sure to go through each line of codes. 

<pre>
<code>
var mraa = require("mraa");
console.log("MRAA version: " + mraa.getVersion()); // see version

var a = new mraa.Aio(0);

captureTemperature();

function captureTemperature() {
	var b = a.read();

	b = b * 0.48826125;
	console.log("Celcius: " + b);

	settimeout( function() {
		captureTemperature();
	}, 4000); // freeze for 4 secs
}
</code>
</pre> 

In this example, we use Intel IoT XDK.

![](/img/lm35-intel-iot-xdk-example.png)

Remember to include 'mraa' library into 'package.json' before build and run the project.

![](/img/lm35-intel-iot-xdk-example-2.png)

## What's Next?

There are a bunch of [examples](https://github.com/intel-iot-devkit/mraa/tree/master/examples) of mraa library implementation. Try it out. APIs documentation is available on [MRAA library documentation](http://iotdk.intel.com/docs/master/mraa/). Once you are familiar with the APIs, you should be able to write your own implementation.

### References:

* [MRAA library on Github](https://github.com/intel-iot-devkit/mraa)

* [Intel IoT: Get Started](/lessons/2015/04/24/cpt2112015-intel-iot-xdk-get-started)
