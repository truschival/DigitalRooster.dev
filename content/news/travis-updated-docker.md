---
title: Travis updated Docker and broke my build :(
date:  2019-10-21T16:29:42+02:00
description: ""
summary: > 
  CI/CD is great, docker avoids implicit dependencies - the build environment 
  is stable, or not so much...
  
  Travis has updated the images and the images changed the Docker
  Version from 17.09.0-ce to 18.06.0-ce - which brakes QT rcc builds :(
keywords: "news"
categories: 
    - "news"
    - "CI/CD"
---

I took up working on DigitalRooster Gui last week, minor fixes, some QML stuff
really nothing big. No new features, no Changes to CMakeLists.txt no changes to
QT resources, no changes to the docker containers, no changes in travis.yml.
When pushing to github I got an email that the build is broken.  Since the build
environment was stable I assumed a glitch - retriggered the build but it was
still broken. 

Somehow RCC (the QT resource compiler) couldn't find files

```
AutoRcc subprocess error
------------------------

The rcc process failed to compile
  "/tmp/checkout/qtgui/externalRes/external.qrc"
into
  "/tmp/build/qtgui/DigitalRoosterGui_autogen/2547SMW2VG/qrc_external.cpp"
Command
-------

/usr/lib/qt5/bin/rcc -name external -o /tmp/build/qtgui/DigitalRoosterGui_autogen/2547SMW2VG/qrc_external.cpp /tmp/checkout/qtgui/externalRes/external.qrc
Output
------
RCC: Error in '/tmp/checkout/qtgui/externalRes/external.qrc': Cannot find file 'IconButton.qml'

```

Time to dig in I ran the same build locally as newly created user, I ran it in
the docker build containers I use on travis. I double checked the versions of
libraries and QT I replayed every single step an could not reproduce
it....  __Whiskey Tango Foxtrott__ !?!

There was an issue when I started using docker, I recalled I also had problems
with RCC.  It is due to missing ``statx()`` system call. This can be fixed
running docker ``--privileged``. This fix also worked for my current problem

Apparently Travis has updated the images and the images changed the Docker
Version from 17.09.0-ce to 18.06.0-ce - on a vintage Ubuntu Xenial 16.04 ?!? 

Thanks alot. 
If you run VM images from 2016 please keep them stable and do not
update packages to new major version.
