---
title: "Install VisualStudioCode on Raspberry Pi"
last_modified_at: 2018-03-17T00:55:06-05:00
categories: 
  - Respberry Pi
tags:
  - Respberry Pi
  - RASPBian
  - VSCode
---

### Installing VSCode on Raspberry Pi running RespBian
Original VSCode providing x86 or 64 .deb files for Debian.
But Pi's architecture is **armhf**. 

So you need to build VSCode by yourself, 
or we can choose to use this instead:

### Code - OSS : Community builds of Visual Studio Code for Raspberry Pi
site : https://code.headmelted.com/

Follow the instruction of Linux-APT instructions or just go to their packageCloud : https://packagecloud.io/headmelted/codebuilds and download the *code-oss_1.14.0-1497990172_armhf.deb* file.

### Example
I'm using this version :
https://packagecloud.io/headmelted/codebuilds/packages/ubuntu/xenial/code-oss_1.14.0-1497990172_armhf.deb

Then choose one of these way to install it :
1.  Install the repository - Review the installation script
```
curl -s https://packagecloud.io/install/repositories/headmelted/codebuilds/script.deb.sh | sudo bash
sudo apt-get install code-oss=1.14.0-1497990172
```
2.  Download the package
```
wget --content-disposition https://packagecloud.io/headmelted/codebuilds/packages/ubuntu/xenial/code-oss_1.14.0-1497990172_armhf.deb/download.deb
```
then manual install that *deb file* on raspbian.


