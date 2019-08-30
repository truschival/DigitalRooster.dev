---
title: "Software"
date: 2019-08-27T13:37:19+02:00
description: "What's inside"
image: software.jpg
keywords: "software"
categories:
    - "software"
draft: false
---

Open source is fun, I love looking under the hood how it works and I love todays
possibility to interact with open source developers. I don't want to imagine
living without open source software.

DigitalRooster is open source software licensed under the
[GPLv3](https://www.gnu.org/licenses/gpl-3.0.html). The software runs on
GNU/Linux and is built using [buildroot](https://buildroot.org/). This means
everyone can see the source and change it to meet their expectations.
DigitalRooster's features are far from perfect and most people have their own
idea of perfect anyway.

[__I encourage you to do so__! Go ahead and fix/adapt/change DigitalRooster!](/pages/contributing)

If you find a bug file a ticket, or even better file a ticket and fix it.  If
you think I have no clue about QT or QML - you are probably right! It was my
first project and I learned a lot with it but I would like to continue learning
from your professional hints - so tell me what can be improved and how!

## The Ingredients

DigitalRooster consists of a few components: a linux kernel, device tree,
libraries, QT and last but not least the graphical interface DigitalRoosterGUI.
It is built using buildroot. Buildroot makes it easy to create a root file
system for an SD-card for your DigitalRooster.

### DigitalRoosterGui

The graphical user interface. You can play around with most functionality on
your host computer. To build and run DigitalRoosterGui you need:

1. The source code. Clone or download it from [github.com/truschival/DigitalRoosterGui](github.com/truschival/DigitalRoosterGui)
2. [CMake >3.10](https://cmake.org/download/)
3. [QT >5.11](https://www.qt.io/download)
4. A recent C++ compiler gcc or Microsoft VisualStudio

Follow the [Readme.md](https://github.com/truschival/DigitalRoosterGui/blob/develop/README.md)
for host-builds


### Buildroot distribution

[Buildroot](https://buildroot.org/) provides the infrastructure like
cross-compiler and required 3rd party components such as QT. 

### Digitalrooster Buildroot external

[Buildroot external](https://github.com/truschival/buildroot_digitalrooster)
 provides our custom extensions to the buildroot base. It adds the
 DigitalRoosterGui package, target-hardware specific configurations and patches
 to other packages.
 
  
 ## Putting it all together
 
 Creating a root file system for an SD-Card is described in the
 [Readme.md](https://github.com/truschival/buildroot_digitalrooster/blob/master/Readme.md)
 
