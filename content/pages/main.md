---
title: "DigitalRooster"
date: 2019-08-27T13:37:19+02:00
description: "Why, What and How"
image: demo_on_hardware.jpg
keywords: "overview"
categories:
    - "overview"
draft: false
---

DigitalRooster the Radio Alarmclock that doesn't suck, or if it does
__you__ are able to improve it.

# Why

First and most important - **because it is fun!**

Did you ever buy a product you really loved for its specs and features and after
some time you found something is missing or doesn't feel right? - Well, so did I.

Ten years ago I got a Terratec Noxon iRadio Cube digital alarm clock with
internet radio and UPNP player. A great gadget, unfortunately it died :( Even
worse - Terratec went out of business and does no longer maintain software.  I
had to find a replacement.

After some research I got an 
[Auna Radio Gaga](https://www.auna.de/Radios/Internetradios/Radio-Gaga-Internetradio-WLAN-LAN-DAB-DAB-UKW-USB-AUX-schwarz-Schwarz.html). 
The sound quality is amazing for a alarm clock, it can play FM Radio, DAB+,
internet streams and podcasts using digital frontier radio service - really neat
features but I missed adding other podcast urls and radio stations. I would love
to hack my Auna and the software... but it turns out you can't (at least not
easily).

It was time to create DigitalRooster. And it was the __perfect chance to learn__
a lot about electronics, CAD, 3D-printing and to get to learn QML.

# What

The minimum I wanted was to listen to podcasts and internet radio when I go to
bed and to get woken up reliably in the morning with my favorite news station -
but only during the week.

I don't want complex controls with many buttons but I wanted a physical volume
controler and on/off button, It feels more intuitive to me to turn a knob to
change the volume than fiddling with virtual sliders on a touch display.  So the
hardware got a fancy Grayhill rotary encoder with push button and a touch
display (capacitive). See more in the [hardware](/pages/hardware) section.

First the core functionality of DigitalRoosterGui was developed running on
Debian GNU/Linux and Microsoft Windows as a library that could be tested
independently. The QML GUI came next.

Porting it to embedded Linux with Buildroot on Raspberry Pi was relatively easy.
I had past experience with board support packages and buildroot from previous
projects. Playing around with Raspberry Pi Zero W using framebuffer copy (fbcp)
the performance was o.k. but not overwhelming. I am working on a port to 
Banana Pi M2 Zero with quad-core CPU and a MALI GPU. On Mali/Lima there are 
some quirks with QT shaders but we will figure it out.

At the moment I am working on an extension circuit board that will combine all
audio DAC, amplifier, realtime clock and some PWM on one board. If the hardware
works and can be produced at a reasonalble price I intend to make it available
to you. Stay tuned.  In the mean time tou can already build your own
DigitalRooster with components available from Adafruit.

__I think it is mature enough to share it with *you*__ 

# How

Look at the section [software](/pages/software) and clone the main project from
[github](https://github.com/truschival/DigitalRoosterGui) you can build the
project on your host PC. If you like what you see look at the
[hardware](/pages/hardware) and run it on your Raspberry Pi.

If you are not into coding look in the the section
[contributing](/pages/contributing) there are plenty of ways of collaboration.

