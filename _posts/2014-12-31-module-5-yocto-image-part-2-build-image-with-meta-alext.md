---
layout: post
title: "Module 5: Yocto Image (Part 2) - Build Image with meta-alext"
description: ""
category: Lessons
tags: [Galileo, Module-5]
---
{% include JB/setup %}

This guide shows a step-by-step on how to build Yocto image using *meta-alext* recipes.

![](/img/meta-alext-github.png)

# Pre-requisites

Before you start, make sure that you have fulfill all these requirements:

* A Linux PC host (we use Ubuntu 12.04).
* A stable network connection.

Install some dependencies:

<pre>
<code>$ sudo apt-get install build-essential git diffstat texinfo gawk chrpath file git-core coreutils unziplibsdl1.2-dev desktop-file-utils autoconf automake libtools p7zip-full</code>
</pre>

## 1. Get Quark BSP (1.0.1) package

Download an official Quark BSP (1.0.1) package from Intel page: 

[[http://downloadmirror.intel.com/23197/eng/Board_Support_Package_Sources_for_Intel_Quark_v1.0.1.7z]](http://downloadmirror.intel.com/23197/eng/Board_Support_Package_Sources_for_Intel_Quark_v1.0.1.7z)

## 2. Prepare *meta-clanton*

Unpack *BSP* package:

<pre>
<code>$ 7z x Board_Support_Package_*.7z</code>
</pre>

Unpack *meta-clanton*

<pre>
<code>$ tar xzvf meta-clanton_v1.0.1.tar.gz</code>
</pre>

Go into *meta-clanton* directory.

<pre>
<code>$ cd meta-clanton_v1.0.1/</code>
</pre>

## 3. Add Alext layer

Clone alext recipes into *meta-clanton*.

<pre>
<code>$ git clone https://github.com/alext-mkrs/meta-alext-galileo</code>
</pre>

## 4. Run Setup

<pre>
<code>$ ./setup.sh -e "meta-alext-galileo"</code>
</pre>


