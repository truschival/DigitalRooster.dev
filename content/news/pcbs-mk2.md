---
title: "DigitalRooster Mk2A"
date:  2020-02-01T19:58:18+01:00
description: ""
summary: >
  PCBway did a great job with my first assembly and I am pretty proud of my
  first design- everything works. That being said there is room for
  improvement. But this is stuff you find out by experiment, especially if you 
  have never done it before. 
image: "PCB-Mk2A.webp"
keywords: "news"
categories:
    - "news"
    - "hardware"
---

Complexity is an addictive feature. Once you have build something complex that
works you are proud of yourself. Telling everyone "look what great job I have
done mastering this complex technology". When you realize that there is also an
easier way to do the same it is hard to scrap your work. After all you will have
nothing to show later.

Digitalrooster-MK2A had this problem with the shutdown circuit. To avoid popping
noise of the MAX98357A audio codecs I came up with a low time delay filter that
was intended to deassert the shutdown signal of the chips after a short delay
when I2S bitclock was running.\\
First it didn't really work because the delay was too short - this I fixed by
increasing the capacitance of the low-pass.\\
Second this entire circuit was not necessary. The
[Linux driver for MAX98357A](https://www.kernel.org/doc/Documentation/devicetree/bindings/sound/max98357a.txt)
includes support for a shutdown line. By sacrificing one GPIO I was able to
eliminate an IC and a bunch of passive components.

Once more I realized that Raspberry Pi with Raspbian and Adafruit hardware is
not targeted for experienced embedded engineers. The Speakerbonnet I used so far
does not wire the shutdown pin to a GPIO. What did suprise me even more the
[documentation](https://learn.adafruit.com/adafruit-speaker-bonnet-for-raspberry-pi/raspberry-pi-usage)
tells to use a device tree overlay for ``hifiberry-dac``. This board uses a
different audio codec, compatible but different.

Another issue we faced were slightly different display assemblies. There several
almost identical capacitive PiTFT2.8"!

*   Adafruit  PiTFT2.8" part no 2423 _with_ gpio buttons
*   Adafruit  PiTFT2.8" part no 1983 _without_ gpio buttons

While I was using the one without GPIO buttons. My friend bought the one with
buttons. The buttons interfere with the Pins used for the rotary encoder.

I finished a new design and layout "DigitalRooster-Mk3A" and placed an order
with pcbway.com. Unfortunately they are also affected by the Corona virus
pandemic and assembly lead times have increased to 55-60 days. Maybe beginning
of May I will receive a the order.

The manufacturing costs for prototype quantities are still considerable and not
suited for small series. At the moment the PCB assembly is 40$ without
taxes. This is mainly driven by component costs, especially the fancy 
[Amphenol 89898-320LF](https://www.digikey.de/product-detail/de/amphenol-icc-fci/89898-320LF/609-3054-ND/1535223) 
 40 pin SMD header that can be plugged form top or bottom  (>5 US$)!


