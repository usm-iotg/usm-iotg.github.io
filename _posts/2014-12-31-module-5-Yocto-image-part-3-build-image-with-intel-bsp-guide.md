---
layout: post
title: "Module 5: Yocto Image (Part 3) - Build Image with Intel BSP Guide"
description: ""
category: Lessons
tags: [Galileo, Module-5]
---
{% include JB/setup %}


This guide shows a step-by-step on how to build Yocto image using Intel BSP guide.

![](/img/bsp-guide.png)

Detail documentation PDF can be found [here](http://downloadmirror.intel.com/23197/eng/Quark_BSP_BuildandSWUserGuide_329687_006.pdf)

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

## 2. Prepare BSP Patches

Download *BSP Patches and Build Instruction* package:
[[http://downloadmirror.intel.com/24355/eng/BSP-Patches-and-Build_Instructions.1.0.4.tar.bz2]](http://downloadmirror.intel.com/24355/eng/BSP-Patches-and-Build_Instructions.1.0.4.tar.bz2)

Untar the package:

<pre>
<code>$ tar -xvjf BSP-Patches-and-Build_Instructions.1.0.4.tar.bz2</code>
</pre>

## 3. Prepare *meta-clanton*

Unpack *BSP* package:

<pre>
<code>$ 7z x Board_Support_Package_*.7z</code>
</pre>

Unpack *meta-clanton*

<pre>
<code>$ tar xzvf meta-clanton_v1.0.1.tar.gz</code>
</pre>

## 4. Run *setup.sh*

Go into *meta-clanton* directory and run setup:

<pre>
<code>$ cd meta-clanton_v1.0.1/</code>
<code>$ ./setup.sh</code>
</pre>

## 5. Apply Patches

Apply some patches in recipes. Just copy-paste the commands into terminal and execute. 

#### 5.1 x264 Patch

<pre>
<code>$ sed -i 's|1cffe9f406cc54f4759fc9eeb85598fb8cae66c7|bfed708c5358a2b4ef65923fb0683cefa9184e6f|' meta-oe/meta-oe/recipes-multimedia/x264/x264_git.bbx264</code>
</pre>

#### 5.2 OpenCV Patches

<pre>
<code>$ sed -i 's|OpenCV-|opencv-|' meta-oe/meta-oe/recipes-support/opencv/opencv_2.4.3.bb</code>

<code>$ sed -i 's|^SRC_URI =.*|SRC_URI = "https://github.com/Itseez/opencv/archive/${PV}.tar.gz \\|' meta-oe/meta-oe/recipes-support/opencv/opencv_2.4.3.bb</code>

<code>$ sed -i 's|c0a5af4ff9d0d540684c0bf00ef35dbe|744cbab090783905620da068c25e7f89|' meta-oe/meta-oe/recipes-support/opencv/opencv_2.4.3.bb</code>

<code>$ sed -i 's|f8fbe985978d4eae73e8c3b526ed40a37d4761d2029a5b035233f58146f6f59b|99786101446911cbb0c01761364c7c5eabd6a5df4f35cf88388dbec9bbd998c3|' meta-oe/meta-oe/recipes-support/opencv/opencv_2.4.3.bb</code>
</pre>

#### 5.3 UART Patches

<pre>
<code>$ cp ../patches/uart-1.0.patch meta-clanton-bsp/recipes-kernel/linux/files/</code>
<code>$ echo 'SRC_URI += "file://uart-1.0.patch"' >> meta-clanton-bsp/recipes-kernel/linux/linux-yocto-clanton_3.8.bb</code>
<code>$ cp ../patches/uart-reverse-8.patch ../.</code>
<code>$ patch -p1 < ../uart-reverse-8.patch</code>
</pre>

#### 5.4 USB Patches

<pre>
<code>$ cp ../patches/1.usb_improv_patch-1.patch meta-clanton-distro/recipes-galileo/galileo-target/files/</code>
<code>$ echo 'SRC_URI += "file://1.usb_improv_patch-1.patch"' >> meta-clanton-distro/recipes-galileo/galileo-target/galileo-target_0.1.bb</code>
<code>$ cp ../patches/GAL-118-USBDeviceResetOnSUSRES-2.patch meta-clanton-bsp/recipes-kernel/linux/files/</code>
<code>$ echo 'SRC_URI += "file://GAL-118-USBDeviceResetOnSUSRES-2.patch"' >> meta-clanton-bsp/recipes-kernel/linux/linux-yocto-clanton_3.8.bb</code>
</pre>

#### 5.5 CLLoader Patches

<pre>
<code>$ cp ../patches/2.GAL-193-clloader-1.patch meta-clanton-distro/recipes-galileo/galileo-target/files/</code>
<code>$ echo 'SRC_URI += "file://2.GAL-193-clloader-1.patch"' >> meta-clanton-distro/recipes-galileo/galileo-target/galileo-target_0.1.bb</code>
</pre>

#### 5.6 SPI Upgrader Patches

<pre>
<code>$ cp ../patches/3.GAL-199-start_spi_upgrade-1.patch meta-clanton-distro/recipes-galileo/galileo-target/files/</code>
<code>$ echo 'SRC_URI += "file://3.GAL-199-start_spi_upgrade-1.patch"' >> meta-clanton-distro/recipes-galileo/galileo-target/galileo-target_0.1.bb</code>
</pre>

#### 5.7 OpenSSL Patches

<pre>
<code>$ mv poky/meta/recipes-connectivity/openssl/openssl-1.0.1e    poky/meta/recipes-connectivity/openssl/openssl-1.0.1h</code>
<code>$ mv poky/meta/recipes-connectivity/openssl/openssl_1.0.1e.bb poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
<code>$ sed -i 's|66bf6f10f060d561929de96f9dfe5b8c|8d6d684a9430d5cc98a62a5d8fbda8cf|' poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
<code>$ sed -i 's|f74f15e8c8ff11aa3d5bb5f276d202ec18d7246e95f961db76054199c69c1ae3|9d1c8a9836aa63e2c6adb684186cbd4371c9e9dcc01d6e3bb447abf2d4d3d093|' poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
<code>$ sed -i 's|file://openssl-fix-doc.patch||' poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
<code>$ sed -i 's|file://0001-Fix-for-TLS-record-tampering-bug-CVE-2013-4353.patch||' poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
<code>$ sed -i 's|file://0001-Fix-DTLS-retransmission-from-previous-session.patch||' poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
<code>$ sed -i 's|file://0001-Use-version-in-SSL_METHOD-not-SSL-structure.patch||' poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
<code>$ sed -i 's|file://CVE-2014-0160.patch||' poky/meta/recipes-connectivity/openssl/openssl_1.0.1h.bb</code>
</pre>

#### 5.8 WiFi Patch

<pre>
<code>$ echo 'IMAGE_INSTALL += "linux-firmware-iwlwifi-6000g2b-6"' >> meta-clanton-distro/recipes-core/images/image-full.bb</code>
</pre>

#### 5.9 Sketch Download

<pre>
<code>$ cp ../patches/4.MAKER-222-Sketch_download_unstable-5.patch meta-clanton-distro/recipes-galileo/galileo-target/files/</code>
<code>$ echo 'SRC_URI += "file://4.MAKER-222-Sketch_download_unstable-5.patch"' >> meta-clanton-distro/recipes-galileo/galileo-target/galileo-target_0.1.bb</code>
</pre>

## 6. Resize Image

For this purpose of image, increase the size of image (from 300Mb into 3GB) in order to give more spaces for the image. 

Open *image-full.bb* file in */meta-clanton_v1.0.1/meta-clanton-distro/recipe-core/images/* directory, then edit this line:

<code>IMAGE_ROOTFS_SIZE = "3072000"</code>

## 7. Build the Image

Execute this commands:

<code>$ source poky/oe-init-build-env yocto_build/</code>

<code>$ bitbake image-full-galileo</code>

![](/img/bitbake.png)

**Building the image may take times to complete.*

Upon successful build, you may see something shown below:

![](/img/bitbake-2.png)

If build failed, **trace the errors** which may lead for re-build. Example of failed build is shown below:

![](/img/bitbake-3.png)

## 8. Prepare Micro-SD Card

Go to *meta-clanton_v1.0.1/yocto_build/tmp/deploy/images/* directory and copy these items into SD card:

* <code>boot</code> directory
* <code>bootia32.efi</code>
* <code>bzImage-3.8.r0-clanton-*.bin</code>
* <code>core-image-minimal-initramfs-clanton-*.cpio.gz</code>
* <code>grub.efi</code>
* <code>image-full-galileo-clanton-*.ext3</code>

![](/img/copy-sd-card.png)

And finally rename these files:

* <code>bzImage-3.8.r0-clanton-*.bin</code> into <code>bzImage</code>
* <code>core-image-minimal-initramfs-clanton-*.cpio.gz</code> into <code>core-image-minimal-clanton.cpio.gz</code>
* <code>image-full-galileo-clanton-*.ext3</code> into <code>image-full-clanton.ext3</code>

Put SD card into SD slot in Galileo board and boot your image.

![](/img/insert-sd.png)











