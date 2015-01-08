---
layout: post
title: "Module 4: Galileo - Input/Output"
description: ""
category: Lessons
tags: [Galileo, Module-4]
---
{% include JB/setup %}

This post will introduce basic I/O (Input and Output) with Intel Galileo. Besides we will also introduce digital and analog pins. Figure below shows digital and analog pins of Galileo. 

![](/img/digital-analog-galileo.png)

## Activity 1

A. How many digital pins are available on Galileo?

B. How many analog pins are available on Galileo?

# 1. Digital Pins

In this guide, we will explore <code>pinMode()</code>, <code>digitalRead</code> and <code>digitalWrite</code> APIs. 

### 1.1 <code>pinMode()</code>

We use <code>pinMode()</code> to configure the specified pin either to behave as an input or an output. 

**Syntax**

<code>pinMode(pin, mode)</code>

where:

* <code>pin</code>: the number of pin to set.
* <code>mode</code>: INPUT, OUTPUT, or INPUT_PULLUP. 
* return: node.

### 1.2 <code>digitalRead()</code>

<code>digitalRead()</code> is used to read the value from specified digital pin. 

**Syntax**

<code>digitalRead(pin)</code>

where:

* pin: the number of digital pin to read.
* return: *HIGH* or *LOW*.

### 1.3 <code>digitalWrite()</code>

<code>digitalWrite</code> is used to write a *HIGH* or *LOW* value to a digital pins.

**Syntax**

<code>digitalWrite(pin, value)</code>

where:

* pin: the pin number to write to.
* value: *HIGH* or *LOW* 

## Activity 2

Turn off a built-in LED of Galileo (pin 13) while pressing the pushbutton (pin 2).

Hook up and assemble the components as shown below:

![](/img/activity-2.png)

Open Button (*File > Examples > 0.2 Digital > Button*) example.

![](/img/example-button.png)

Source code:

![](/img/example-button-code.png)

Compile and upload the sketch. 

![](/img/example-button-compile-upload.png)

Press pushButton and observe either that action turns on or turn off the built-in LED.

A. When button is pressed, LED turns ___

B. When button is released, LED turns ___

## Activity 3

Print out the value of pushButton through *Serial Monitor*.

*Hint:*

Use [Serial](http://arduino.cc/en/reference/serial) API to display output in *Serial Monitor*.

* Add <code>Serial.begin(9600); </code> in *Setup* function.
* Add <code>Serial.print(buttonState); </code> in *Loop* function.

A. What is the value of <code>buttonState</code> when button is not pressed? ___

B. What is the value of <code>buttonState</code> when button is pressed? ___

### 1.2 INPUT_PULLUP

Pin default as INPUT. So When pin is disconnect, it randomly read HIGH and LOW. For Example, when wiring buttons or switches or anything that "normally open", we have to tie them to the ground. A 10K Ohm resistor can acts as pull-down resistor for digital input pin. 

## Activity 4

Turn on the built-in LED (pin 13) while pressing pushButton (pin 2). 

Hook up all components as shown below:

![](/img/example-pullup.png)

Open Button (*File > Examples > 0.2 Digital > DigitalInputPullup*) example.

![](/img/example-pullup-3.png)

Source code:

![](/img/example-pullup-code.png)

Compile and upload the sketch.

![](/img/example-pullup-compile-upload.png)

Press pushButton and observe either that action turns on or turn off the built-in LED.

A. When button is pressed, LED turns ___

B. When button is released, LED turns ___

# 2. Analog Pins

In this guide, we will explore <code>analogRead()</code> and <code>analogWrite()</code> APIs.

### 2.1 <code>analogRead()</code>

We use <code>analogRead()</code> to read the value from the specified analog pin.

**Syntax**

<code>analogRead(pin)</code>

where:

* <code>pin</code>: the number of analog pin to read.
* return value: int (0 to 1023)

### 2.2 <code>analogWrite()</code> (PWM)

We use <code>analogWrite()</code> to write an analog value (PWM wave)to a pin.

**Syntax**

<code>analogRead(pin, value)</code>

where:

* <code>pin</code>: the number of analog pin to write to.
* <code>value</code>: the duty cycle (between 0(always off) and 255(always on)).
* return: nothing.

### 2.1 PWM (Pulse-Width-Modulation)

Description

In simple description, PWM produces output analog results but with digital means and PWM is not a *pure* analog output. 

## Activity 5

Use PWMto fade the LED. 

Hook up all components as shown below:

![](/img/example-pwm.png)

Open Button (*File > Examples > 0.3 Analog > Fading*) example.

![](/img/example-pwm-2.png)

Source code:

![](/img/example-pwm-code.png)

Compile and upload the sketch.

![](/img/example-pwm-compile-upload.png)

Observe the fading of the LED. Explain how the source code works. 

## Activity 6

Use potentiometer to fade the LED.

Potentiometer has 3 pins:

* Pin 1: connect to GND
* Pin 2: connect to analog pin 3
* Pin 3: connect to 5V

Hook up the components as shown below:

![](/img/example-potentiometer.png)

Source code:

![](/img/example-potentiometer-code.png)

Compile and upload the sketch.

![](/img/example-potentiometer-compile-upload.png)

Fade in and out of LED using potentiometer. 

A. Refer source code, at line <code>analogWrite(ledPin, val / 4);</code>, why we divide <code>val</code> by 4? ___

# Small Project

Blink an LED with pushButton. While pressing the pushButton, the interval of the blinking should be adjustable by potentiometer. Once you release the pushButton the LED should turns off. 

![](/img/small-project.png)

