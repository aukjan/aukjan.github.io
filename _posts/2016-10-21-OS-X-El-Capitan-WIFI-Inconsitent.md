---
layout: post
title: OS X El Capitan WiFi not working consitently
excerpt_separator: <!--more-->
---

You have a good functioning WiFi network at home, all devices are working correctly, but your MacOS laptop has a continuously flaky network connection. What to do ... 

<!--more-->

This manifests itself not alwasy, but when it does it is consistent. The following picture tells a thousand words...

![Ping Google](/public/img/ping_to_google.png)

So .. how to fix this?  Magic! 

As referenced here [https://discussions.apple.com/thread/1208774?start=0&tstart=0](https://discussions.apple.com/thread/1208774?start=0&tstart=0) , you need to remove `/Library/Preferences/SystemConfiguration/com.apple.airport.preferences.plist` (don't worry, it will be created again), and reboot your mac. Now the WiFi connection will be stable again.