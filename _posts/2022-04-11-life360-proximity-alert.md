---
layout: post
title: "Life360 Proximity Alert"
subtitle: "A tool I made for Senior Assasain."
tags: ""
---

## Life360 Proximity Alert
### A tool I made for Senior Assasain

So, I made a new thing yesterday.

I was invited to a game of 'Senior Assasain,' which, if you are unaware, is a traditional high school senior game played toward the end of term that is basically a week-long water gun fight. You get a target to elimitate, but you have a target on your back. You do not know who, and they may show up at any time at any place.

So obviously my first thought was, "How do I win?"

The solution I came up with was this: a program that would let me know, via Apple Watch/iPhone notifications, if someone in the game was within ~.1 of a mile of me. That would allow me to get to cover, get my safety item (wearing swim googles, it makes you 'safe'), or even retalliate with a garden hose.

I couldn't figure out any of the existing Life360 libraries in Python, so I just made my own interface. It wasn't that hard:

#### Step 1: Intercept API requests.
I connected my iPhone to Burp Suite to allow me to sniff Life360 traffic. By the way, Burp Suite is COOL. SSL decryption is kind of fun, and I hope to use it more to crack more apps n the future,

