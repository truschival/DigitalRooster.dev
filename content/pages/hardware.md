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
## Electronics

Currently DigitalRooster is built from these Components:

* Raspberry Pi Zero W (without soldered header)
* Long (15mm) 2.54mm connection header to stack the extension boards on the Raspberry Pi
  [(Digikey 3M156504-72-ND)](https://www.digikey.de/products/de?keywords=3M156504-72-ND)
* Adafruit [PiTFT2.8" capacitive touch](https://learn.adafruit.com/downloads/pdf/adafruit-2-8-pitft-capacitive-touch.pdf)
* Adafruit [Speaker Bonnet with MAX98357 I2S amp](https://cdn-learn.adafruit.com/downloads/pdf/adafruit-speaker-bonnet-for-raspberry-pi.pdf)
  [(Digikey 1528-1819-ND)](https://www.digikey.de/products/de?keywords=1528-1819-ND)
* Grayhill rotary encoder [61C11-01-08-02](http://lgrws01.grayhill.com/web1/images/ProductImages/I-21-22.pdf)
  [(Digikey GH6102-ND)](https://www.digikey.de/products/de?keywords= 61C11-01-08-02)
* Kilo International knurled knob OEDNI-90-3-5
  [(Digikey 226-4201-ND)](https://www.digikey.de/products/de?keywords=OEDNI-90-3-5)

The total cost is about 120U$ on digikey while the rotary encoder alone accounts
for 25US$.

### Caveats

The Raspberry Pi has few hardware PWM pins. One is used for SPI, the other one I
would like to use for Backlight control. Unfortunately the Pin is right next to
the I2S pin for the speaker bonnet and may cause interference when connected
through the speaker bonnet. As a quick fix I just cut the pin and soldered a
flying wire from the Pi to the backlight pad of the TFT - not the most
professional way to deal with EMI issues but it remedies the noise on the
speakers.

## Upcoming hardware

I am working on (my first) design of an extension PCB with three audio channels,
integrated RTC, I2C PWM driver for backlight and possible LED illumination.
This will also remedy the caveats and should work on Raspberry Pi and Banana Pi.

### First Attempt
<img src="/img/pages/Board3d.jpg" alt="rendering of green pcb"
	title="first attempt pcb" class="image small" />

The schematics are done. The first layout was sent to
[JLCPCB](https://jlcpcb.com) and the is on the way. But this won't help I
realized some layout issues about an hour after placing the order...  The main
issue was that I switched I2C SDA and SCL on the real time clock. I am an
electrical engineer by trade and even had a lecture on embedded systems design
where we heard about some layout rules. But apparently I didn't tap into that
knowledge and neither did I read all the layout hints given by Maxim for the RTC
IC. In the end I ran the I2C Clock trace beneath the oscillator.... bad idea.

However I learned a lot with this failure. For instance it it not easy to solder
SMD with solder paste and solder iron. Soldering with solder iron works better
with wire.

I made some experiments with my messed up half-way hand soldered board in the
baking oven to calibrate the temperature and time and it works amazingly well!

Preheat the oven to 205°C (or at least that what I can adjust with the turning
knob). Put the PCB for 3:20 minutes and you get a reasonable result.  It didn't
even kill the ICs, or at least not all of them. The I2C port expander MAX7315
survived the procedure. I don't know if it was the heat, solder errors or layout
mistakes but sound didn't work.

### Second Attempt

I made a range of improvements to the PCB. Not only to the layout but also to
the schematics. I double checked my wiring and components, replaced the 5US$
Maxim DS1388 real time clock with a cheaper TI BQ32000.

<img src="/img/pages/DigitalRooster-Mk2a.webp" alt="rendering of red PCB"
	title="second attempt pcb" class="image small" />

Replaced THT components with SMD and sent it to
[pcbway.com](https://www.pcbway.com) for quotation.  The BOM quotation is
absolutely fair priced! The price is comparable to digikey for small numbers. At
the moment they run discounts for assembly, for a five prototype PCBs they also
only charge 30$ setup costs - dirt cheap!

I gave it a placed the order yesterday - lets wait and see, ETA is 25 days.

## Casing

The housing is printed on a Prusa MK3. You can find the STL-files here.  Make
sure you scale the housing with about 0.5% so the side panels fit in. otherwise
you will have problems mounting.
