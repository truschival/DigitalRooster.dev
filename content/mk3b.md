---
title: "DigitalRooster MK3b"
date: 2020-07-19T12:40:48+02:00
description: "The PCB I wanted"
summary: >
        Mk3b is the board I wanted. I think it is ready for mass production!
categories:
   - "hardware"
---

<img src="/img/news/mk3b-assembled.webp" 
     alt="fully assembled PCB of DigitalRooster mk3b" 
	 title="DigitalRooster-mk3b" class="image small" />

## Introduction

The hardware is designed to works both with Raspberry Pi Zero W and Banana Pi M2
Zero. To work with any of these two boards requires
[soldering some jumpers](#solder-jumpers).

**Note:** The Mk3b-extension board is a module without independent function, and
is exclusively intended for development or education purposes under laboratory
conditions. For use or operation specialist knowledge is required. Please
observe the necessary regulations and the general [safety and environmental
notes](/pages/safety)

## Schematic

The **[schematic PDF](/schematic-mk3b.pdf)** contains some additional notes on
optional components and solder jumpers.
<a href="/schematic-mk3b.pdf"> <img
src="/img/schematic_abstract.webp" alt="screenshot of a schematic"
title="schematic digitalrooster-mk3b" class="image small" /> </a>

## Solder Jumpers

**Warning:** Soldering can cause injuries and requires some skills. The solder
iron is hot and solder fumes are hazardous! Please also read the [safety and
environmental notes](/pages/safety)


<img src="/img/news/mk3b-back.webp" alt="PCB bottom side with solder jumpers"
	title="DigitalRooster-mk3b back" class="image small" />

### Raspberry Pi

To connect the I2S lines to the correct pins you have to solder jumper **JP2**
and **JP3** to position **1-2** (the small triangle marks pad 1)

You **must not solder JP4** This jumper connects the back-light dimming to GPIO
pin 12 which Raspberry Pi unfortunately uses for I2S bit clock. You have to
solder a wire from J5 pin 6 to the backlight pwm control input of your display.
Unfortunately the Raspberry Pi SoC BCM2708 has few PWM lines and

Do not solder JP1.

### Banana Pi

To connect the I2S lines to the correct pins you have to solder jumper **JP2**
and **JP3** to position **2-3** (the small triangle marks pad 1)

You can/should solder **JP4** This jumper connects the PWM output to the
back-light pin of your [PiTFT2.8" capacitive
touch](https://learn.adafruit.com/downloads/pdf/adafruit-2-8-pitft-capacitive-touch.pdf)
Some of the PiTFTs also have a solder jumper to enable back-light dimming.

You must **solder JP1**. This jumper is a workaround for Banana Pi. The
Allwinner H2+ SoC unfortunately has no IRQ line on PC4. Adafruit designed the
PiTFT to use pin 18 as IRQ for the touch sensor. This jumper maps PC4 (pin 18)
to PL4 (pin 26) which has interrupt functionality.

## FAQ

1.  **During boot I see errors for failing oscillator of the real time
    clock!**.\
	You may come across this message
	```
	[    0.789186] bq32k 1-0068: Oscillator Failure. Check RTC battery.
    [    0.796005] bq32k 1-0068: Enabled trickle RTC battery charge.
    [    0.802898] rtc rtc0: read_time: fail to read: -22
	```
	This is not a false alarm. It happens when you plug in your board
    and the super cap has not yet been charged and hence the RTC is not yet
    backup powered.	**This message will go away after some time.** The trickle
    charger takes some hours to charge the supercap C36.
