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
  [Digikey 1528-1423-ND](https://www.digikey.com/product-detail/en/adafruit-industries-llc/1983/1528-1423-ND/5699178)\
  __Note:__ there are 2 types: with buttons (Mfg Part No. 2423) and without
  buttons (Mfg Part No. 1983). \
  I use the one without buttons
* Adafruit [Speaker Bonnet with MAX98357 I2S amp](https://cdn-learn.adafruit.com/downloads/pdf/adafruit-speaker-bonnet-for-raspberry-pi.pdf)
  [(Digikey 1528-1819-ND)](https://www.digikey.de/products/de?keywords=1528-1819-ND) \
  Wait for the upcoming hardware which will be _*awesome*_.
* Grayhill rotary encoder [61C11-01-08-02](http://lgrws01.grayhill.com/web1/images/ProductImages/I-21-22.pdf)
  [(Digikey GH6102-ND)](https://www.digikey.de/products/de?keywords= 61C11-01-08-02)
* Kilo International knurled knob OEDNI-90-3-5
  [(Digikey 226-4201-ND)](https://www.digikey.de/products/de?keywords=OEDNI-90-3-5)

The total cost is about US$ 120 on digikey while the rotary encoder alone accounts
for 25US$.

### Caveats

The Raspberry Pi has few hardware PWM pins. One is used for SPI for the display,
the other one I would like to use for Backlight control. Unfortunately the Pin
is right next to the I2S pin for the speaker bonnet and may cause interference
when connected through the speaker bonnet. As a quick fix I just cut the pin and
soldered a flying wire from the Pi to the backlight pad of the TFT - not the
most professional way to deal with EMI issues but it remedies the noise on the
speakers.

## Upcoming hardware DigitalRooster-MK3A

The third prototype of an extension PCB will have:

*   three audio channels with analog filters
    _way_ better sound
*   a hardware shutdown line for the audio codecs so 'off' is really 'off' and
    there is no popping noise when changing tracks turning on.
*   Integrated Real Time Clock
*   I2C PWM LED driver for back-light and possible LED illumination.
    So you can wake up with a nice artificial sunrise next to your bed.
*   external I2C connection with interrupt line to support e.g. APDS9660 gesture
    and light sensor for dynamic back-light control and gesture snooze.

This will also be compatible with both Raspberry Pi _and_ Banana Pi. So you have
a wider choice of more powerful hardware!

<img src="/img/news/DigitalRooster-Mk2a.webp" alt="rendering of red PCB"
	title="second attempt pcb" class="image small" />

## Casing

The housing is printed on a Prusa MK3. You can find the STL-files here.  __Make
sure you scale the housing with about 0.5%__ so the side panels fit in otherwise
you will have problems mounting.
