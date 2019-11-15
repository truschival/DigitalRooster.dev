---
title: "PCBs from China have arrived!"
date:  2019-09-04T19:44:16+02:00
description: ""
summary: >
  The time from order to delivery was amazingly quick.
  JLCPCB has real human customer care!
keywords: "news"
image: "pcb_rev1.jpg"
categories:
    - "news"
    - "hardware"
---

I got my first batch PCBs from [JLCPCB](www.jlcpcb.com) in less than two weeks
choosing low-priority shipping.
I ordered five 2-layer PCBs with a laser cut stencil.

The service of JLCPCB was surprisingly good. I never thought these orders for
5U$ would be checked by a human being but during manufacturing I was contacted
by a person called Tony Lee inquiring about the backside stencil. I haven't
included back side solder mask since there are no components except for some
THTs and solder jumpers that require soldering.

Unfortunately even the best PCB manufacturer cant fix my layout errors - reading
the datasheets and thinking for 5ct would have spared me some issues with the
layout:
 1. You should not run signals, especially clock lines, below the wires of
    a crystal for the Real Time Clock. These crystals work at µW level and are
    sensitive to cross-talk.
 2. You should read the datasheet of your RTC, if it says 6pF Load capacitance,
    buy a 6pF Crystal and not a 12pF Crystal.

and there are probably some more issues I haven't found yet.....

All in all I payed 12US$ to learn the hard way to pay more attention.

However I learned a lot with this failure. For instance it it not easy to solder
SMD with solder paste and solder iron. Soldering with solder iron works better
with wire.

<img src="/img/news/pcb_1_pre_oven.webp" alt="mountin SMD on a PCB by hand"
	title="populating the PCB" class="image small" />

I made some experiments with my messed up half-way hand soldered board in the
baking oven to calibrate the temperature and time and it works amazingly well!

<img src="/img/news/pcb_1_in oven.webp" alt="a PCB in the baking oven"
	title="in the oven" class="image small" />

Preheat the oven to 205°C (or at least that what I can adjust with the turning
knob). Put the PCB for 3:20 minutes and you get a reasonable result.  It didn't
even kill the ICs, or at least not all of them. The I2C port expander MAX7315
survived the procedure. I don't know if it was the heat, solder errors or layout
mistakes but sound didn't work.

<img src="/img/news/pcb_1_assembled.webp" alt="oven soldered PCB"
	title="the result" class="image small" />
