---
title: "PCBsfrom China have arrived!"
date:  2019-09-04T19:44:16+02:00
description: ""
summary: "The time from order to delivery was amazingly quick. JLCPCB has real human customer care!"
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
