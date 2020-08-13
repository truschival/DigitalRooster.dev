---
title: "Hardware"
date: 2019-08-27T13:37:19+02:00
description: "DigitalRooster Hardware"
slug: "hardware"
keywords: "hardware"
categories:
    - "hardware"
    - "electronics"
draft: false
---

The initial prototype was built using a Raspberry Pi Zero an Adafruit PiTFT and
Speaker Bonnet plus some circuitry on a prototyping PCB. This works but had a
range of serious drawbacks. For instance the Speaker Bonnet does not have a gpio
connected to the shutdown pin of the codec which leads to a nasty popping noise
when changing tracks. I also required some circuitry to adapt the voltage levels
of the rotary encoder to 3.3V, I also wanted a real time clock.

But most important: I have been an electrical engineer since 2008 but I have
never designed a PCB this was my chance to learn electronic design!

## DigitalRooster-Mk3b extension board

<img src="/img/news/mk3b-assembled.webp" 
     alt="fully assembled PCB of DigitalRooster mk3b" 
	 title="DigitalRooster-mk3b" class="image small" />

The hardware design started in 2019. I was ordering PCBs and imagined hand
assembly for the prototypes. Not only was the design unnecessarily complicated,
it also had a pretty bad layout and I had to admit my soldering skills do more
damage than good. PCBWays turnkey assembly was the way to go. However I still
needed two iterations to get what I wanted. Probably an experienced electronics
hardware engineer would find many possibilities for improvement, especially for
layout and component costs. But I am happy so far. With the Mk3b I finally got
the board I wanted.  \
I also think it is ready for mass production and to share
it with you on [tindie.com](https://www.tindie.com/products/21067/)!

### Features
-   Three Channel audio using a 3W MAX98357A I2S driver. Since this IC is a
    Class-D amp I equipped the channels with passive LC filter to improve audio
    quality. The left/right channels have a cut-off frequency of around 20kHz
    while the mid channel filter is a 16kHz low-pass

-   a hardware shutdown line for the audio codecs so 'off' is really 'off' and
    there is no popping noise when changing tracks

-   A BQ32000 Real Time Clock chip with trickle-charge circuit that charges a
    200mF SuperCap. Although the software synchronizes time using NTP I wanted a
    Real Time Clock in case the network is down. Also having a the correct time
    during boot makes logging a lot more insightful and avoids TLS error for
    certificates that are not yet valid on Jan 1st of 1970...

-   A TLC59208F PWM LED driver for backlight control and a possible RGBA light
    to wake up with a sunrise simulation. The PWM pins on both Raspberry Pi and
    BananaPi are scarce an used for other functions, e.g. I2S. Software PWM is
    not really a nice option so I was willing to spend some 2.5$ for a nice I2C
    chip that integrates nicely with the Linux LED driver framework

-   Integrated circuitry for the Grayhill rotary encoder that requires voltage
    dividers and a debounce for the push button

-   The possiblity to connect an external I2C device. I have a APDS9660 gesture
    and light sensor in mind for dynamic back-light control or gesture snooze.

-   Last but not least: a separate header for UART console since when assembled
    it is hard to access the UART of the Raspberry Pi.

The Mk3b is also compatible with both Raspberry Pi *and* Banana Pi M2 Zero. So
you have a wider choice of more powerful hardware! However Banana Pi M2 Zero
performance is sub-par. It takes ages for the display to react to touch events.
I don't consider the Banana Pi version production ready yet. The Raspberry Pi 
configuration works really nicely.

**Note:** The Mk3b-extension board is a module without independent function and
is exclusively intended for development purposes under laboratory conditions.
For use or operation specialist knowledge is required. Please also read the
[safety and environmental notes](/pages/safety)

For details please refer to the **[schematic-mk3b.pdf](/schematic-mk3b.pdf)**
and the product **[mk3b landing page mk3b](/mk3b)**

### Where to buy

Currently I am selling a kit that requires some soldering on 
[tindie.com](https://www.tindie.com/products/21067/)!

## Other Parts

To build your DigitalRooster you will need some more parts in addition to the
[extension board](#digitalrooster-mk3b-extension-board):

-   Raspberry Pi Zero W (without soldered header)

-   Adafruit [PiTFT2.8" capacitive touch](https://www.adafruit.com/product/1983)\
    **Note:** there are two types sold under the same name: \
    one with buttons (Mfg Part No. [2423](https://www.adafruit.com/product/2423))
    and without buttons (Mfg  Part No. [1983](https://www.adafruit.com/product/1983))\
    I use the 1983 without buttons [(Digikey 1528-1423-ND)](https://www.digikey.com/product-detail/en/adafruit-industries-llc/1983/1528-1423-ND/5699178)

-   Long (15mm) 2.54mm connection header to stack the extension boards on the 
    Raspberry Pi [(Digikey 3M156504-72-ND)](https://www.digikey.de/products/de?keywords=3M156504-72-ND)

-   Grayhill rotary encoder [61C11-01-08-02](http://lgrws01.grayhill.com/web1/images/ProductImages/I-21-22.pdf)
    [(Digikey GH6102-ND)](https://www.digikey.de/products/de?keywords=61C11-01-08-02)

-   Kilo International knurled knob OEDNI-90-3-5
    [(Digikey 226-4201-ND)](https://www.digikey.de/products/de?keywords=OEDNI-90-3-5)

-   Some small speakers ca.3-5W 4&#x2126; for instance [Adafruit
    Speaker](https://www.adafruit.com/product/1314)

I added links to digikey.com, but they serve only as reference you can get them
wherever you like. I do not have any deal with Adafruit or digikey, I just use
it because it is convenient.

The total cost is about US$ 120 (on digikey) while the rotary encoder alone
accounts for 25US$. You can use different components but these are the ones I
have tested so far.

**If you find a nicer rotary-encoder with push-button that turns even smoother
please let me know! I would like one that turns 'notch-less'**

### Assembly
It is not that hard but maybe I will create a photo-guide.

Make sure you [solder the correct jumpers](/mk3b#solder-jumpers)

## Casing

<img src="/img/3D-CAD.webp" alt="3D CAD view of the Casing"
	title="CAD view" class="image small" />

The housing is printed on a Prusa MK3. You can find the
[STL-files here](/parts-stl.7z). \
*Make sure you scale the housing with about 0.5%* so the side panels fit in
otherwise you will have problems mounting.
