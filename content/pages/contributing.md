---
title: "How to contribute"
date: 2019-08-27T13:26:26+02:00
description: "Contributing to DigitalRooster"
slug: "contributing"
keywords: "contributing"
categories: 
    - "contributing"
    - "software"
draft: false
---

There are many ways to contribute to DigitalRoosterGui for *everyone* and all
skills and skill levels. From UI Design to Linux graphics drivers, QT/C++ code
to webui with JS/HTML5 for configuration. If you don't like programming, file a
bug or feature request, write documentation, design a extension circuit board or
nicer case. There are many opportunities for everyone to contribute - The
project needs you!

*  File a Bug
*  File a feature request
*  Submit code for a feature or bugfix
*  Make this ugly website look professional
*  Modify code
*  write documentation
*  write tests
*  port it to other hardware
*  add your own program to run on the DigitalRooster system
*  ... make the thing better

## Contributing to existing code

The easiest way to contribute is to create a github pullrequest against the
develop branch of the subprojects.

*  [DigitalRoosterGui](https://github.com/truschival/DigitalRoosterGui) : QML-Application
*  [DigitalRoosterREST](https://github.com/truschival/DigitalRooster_REST) : a quickhack OpenAPI webservice to
   configure DigitalRoosterGui (this needs professional attention!) 
*  [DigitalRooster.dev](https://github.com/truschival/DigitalRooster.dev) : Source of this website
*  [Buildroot external](https://github.com/truschival/buildroot_digitalrooster) : to build the embedded linux for your hardware.

It is a good idea to open an issue in the respective project beforehand to share
the idea.

If it is C++ Code make sure it is formatted using the ``.clang-format`` file of
the repository. Make sure the code has test-cases and doesn't break existing
test-cases. The code will be reviewed and analyzed. If it meets the quality and
is appropriate it will be merged.

Make sure the code you contribute is 100% your orginal work and you have the
right and will to publish it under DigitalRoosters license [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html).

In other words:

*  Don't steal code from your friends and pretend it's
   yours - that's unethical
*  Don't copy-paste/steal proprietary (patented) code from your
   company - that's illegal
*  If you write code for DigitalRooster on your employers time make sure the 
   company is o.k. with your work being 'highly contageous' GPLv3 copyleft code.

## Create new projects

Buildroot is modular by design. If you have software that should run on the
DigitalRooster system you can easily add a package.

If you have schematics or designs contact DigitalRooster or make a pull-request
against this file to create a link to your project.

