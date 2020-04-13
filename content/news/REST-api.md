---
title: "REST API"
date:  2020-04-13T16:26:08+02:00
description: "DigitalRooster got a REST API"
summary: >
  Not all of us enjoy adding their favorite radio station to the list using vi
  over a serial line. Especially since this is error prone.
  DigitalRoosterGui now provides a simple REST API to add, list and delete
  Alarms, Podcasts and Internet Radio stations.
  The API is specified according to the openapi spec 3.0. This means you can
  create client code automatically form the specification. Now some adapt and
  motivate Front-End developer should take over and implement a nice web-gui...
keywords:
	- "REST"
	- "Configuration"
categories:
    - "news"
    - "software"
---

Openapi really rocks. I have used it at work and it was the first time in my
professional career that I truly had a formal specification that I could turn
into code. At [openapi-generator.tech](https://openapi-generator.tech/) you can
find generators for almost all programming languages. I use it to generate client
code for testing the API.

You find the full API specification in
[REST/openapi.yml](https://github.com/truschival/DigitalRoosterGui/blob/develop/REST/openapi.yml)
Using the [swagger editor](https://editor.swagger.io/) you can even execute
the API calls.

While in another project I also used it to generate server code for
[pistache](http://pistache.io/) I opted against generating server code for
DigitalRoosterGui. I came to the conclusion that the generated C++ code was not
something I wanted to integrate. Partially because it uses a different JSON
library, partially because I couldn't get the generator to use the classes I
already had (Alarm, PodcastSource etc.).

But still it works really nice using ``curl`` to manipulate the lists. You can
find out more in
[documentation/rest.md](https://github.com/truschival/DigitalRoosterGui/blob/develop/documentation/rest.md)

 One small example of how to add a radio station:
 ``` sh
 curl -X POST localhost:6666/api/1.0/radios/ \
    -d "{\"url\":\"http://foo.bar\", \"name\":\"FooRadio\"}"
 ```
