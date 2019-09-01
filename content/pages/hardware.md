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

<img src="/img/pages/Board3d.jpg" alt="new PCB"
	title="new PCB" class="image small" />

The schematics are done. The first layout was sent to
[JLCPCB](https://jlcpcb.com) and the is on the way. But this won't help I
realized some layout issues about an hour after placing the order...

## Casing

The housing is printed on a Prusa MK3. You can find the STL-files here.
