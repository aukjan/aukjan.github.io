---
layout: post
title: OS X El Capitan WiFi Woes
excerpt_separator: <!--more-->
---

So .. you are happily online on your WiFi,  working, video conferening on Skype / GotoMeeting / (pick your vice for online meeting)..., showing off some cool online tools, when suddenly the tool you are showing 'stops working', but your online meeting continues....

Hmmm .. that's weird. You now test the connection by pinging .. 

but all you get is:

```
Request timeout for icmp_seq 6100
Request timeout for icmp_seq 6101
Request timeout for icmp_seq 6102
Request timeout for icmp_seq 6103
Request timeout for icmp_seq 6104
Request timeout for icmp_seq 6105
Request timeout for icmp_seq 6106
Request timeout for icmp_seq 6107
Request timeout for icmp_seq 6108
Request timeout for icmp_seq 6109
Request timeout for icmp_seq 6110
``` 

What's going on?

<!--more-->

After a kill of the WiFi interface, and restarting, you are back online, happiliy showing off the tool again, while the meeting only had a small hickup.  How strange! 

So now there are two options... Dig into the MacOS strangeness of the WiFi connection, or find a workaround to have the system fix itself when this happens... I opt for number two ;) 

The follwing little shell script gem will keep an eye out for flaky connection and fixes it for you:

```
#!/bin/bash
[[ -d ${HOME}/log ]] || mkdir -p ${HOME}/log
echo "$(date) [START] Starting WIFI Watch" >> ${HOME}/log/wifi_reset.log
while [ 1 ]
do 
  ping -c 5 -t 10 8.8.8.8 ||  ( 
    echo "$(date) [RESET] Resetting WIFI connection " >> ${HOME}/log/wifi_reset.log 
    networksetup -setairportpower en0 off
    sleep 5
    networksetup -setairportpower en0 on
    sleep 30
  ); 
done 
```

{% gist 14aa3ebf8bb6824d6515f0e67c71b2ee %}

Now choose your favorite means of running (simple shell script, or wrappes in Automator Application) and voila, no more manual reset of the WiFi connection! 

Oh, and it creates a nice log...

```
Wed Dec 21 14:47:26 CET 2016 [START] Starting WIFI Watch
Wed Dec 21 15:02:04 CET 2016 [RESET] Resetting WIFI connection
Wed Dec 21 15:17:06 CET 2016 [RESET] Resetting WIFI connection
Wed Dec 21 15:17:52 CET 2016 [RESET] Resetting WIFI connection
Wed Dec 21 15:32:16 CET 2016 [RESET] Resetting WIFI connection
Wed Dec 21 16:02:25 CET 2016 [RESET] Resetting WIFI connection
Wed Dec 21 16:32:38 CET 2016 [RESET] Resetting WIFI connection
Wed Dec 21 16:47:43 CET 2016 [RESET] Resetting WIFI connection
```



