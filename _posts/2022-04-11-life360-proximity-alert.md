---
layout: post
title: "Life360 Proximity Alert"
subtitle: "Ping your Apple Watch if people get too close to you. Great for Senior Assassin."
tags: ""
---
I was invited to a game of 'Senior Assasain,' which, if you are unaware, is a traditional high school senior game played toward the end of term that is basically a week-long water gun fight. You get a target to elimitate, but you have a target on your back. You do not know who, and they may show up at any time at any place.

So obviously my first thought was, "What can I do to make sure I win?" We were using Life360, so I figured there had to be a way to improve my odds.

The solution I came up with was this: a program that would let me know, via Apple Watch/iPhone notifications, if someone in the game was within ~.1 of a mile of me. That would allow me to get to cover, get my safety item (wearing swim googles, it makes you 'safe'), or even retalliate with a garden hose.

I couldn't figure out any of the existing Life360 libraries in Python, so I just made my own interface. It wasn't that hard:

I connected my iPhone to Burp Suite to allow me to sniff Life360 traffic. By the way, Once I had the requests coming in, I used the existing libraries on Github as a baseline for learning how the Life360 app interacted with their backend. All I needed was to pass the authentication token along and it would spit out the data I needed.


I then stole a distance calculation algorithm from StackOverflow and used it to calculate the distance of all the people in the circle to me (the first person returned by the API). If the direct distance was within, say, 500 ft, it would send a request to Pushover's API (which by the way is a great app and super easy to use) to let me know. I also programmed a delay, so that it wouldn't send a notification every time it updated position data - it would wait a specified time before letting me know again.

This is about where development ended, however. The game was over before it even started - infighting and the realization that Life360 was way too accurate was clearly too much for the stability of a 30 person group chat. However, I value the learning experience of reverse engineering API requests and intercepting web traffic from my phone.

If you'd like to use my code in your Life360 project, [click here](https://github.com/reecepounder/life360-proximity-alert). I had no luck with the existing Python libraries that claim they can interface with Life360, so if you want to create one from this I encourage you to do so.

