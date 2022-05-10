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

I connected my iPhone to Burp Suite to allow me to sniff Life360 traffic. By the way, Burp Suite is COOL. SSL decryption is kind of fun, and I hope to use it more to crack more apps in the future, because that is super cool. Bye-bye, security through obscurity.

Once I had the requests coming in, I used the existing libraries on Github as a baseline for learning how the Life360 app interacted with their backend. Shout-out to Life360, by the way, for the cool API landing page at (api.life360.com)[https://api.life360.com].

It was pretty straight forward, and the Life360 engineers made it a simple API. But that's the concerning bit - if someone were to pull off an SSL interception attack and get the headers for the GET request, someone could spoof those requests pretty easily. It took me 30 minutes while eating a sandwich. That being said, SSL is tricky to decrypt, but on a corporate network for example? I think this is dangerous because of the data Life360 holds (namely real-time locations). But that's my two cents - I am not, like, a certified cybersecurity expert or anything.

Regardless, at that point I stole a distance calculation algorithm from StackOverflow and compared the GPS co-ordinates of all the people in the circle to the first person returned (the user). If it was within, say, 500 ft, it would send a request to Pushover's API (which by the way is a great app and super easy to use) to let me know. I also programmed a delay, so that it wouldn't send a notification every time it updated position data - it would wait a specified time before letting me know again.

I think something I'd like to add, if Pushover allows it, is the ability to present a live map of my design. But that sounds complicated, and the joke I had developed this for was already over (in fact it never begun. It was a large-scale 7-day water fight, but instead of using Life360 which was deemed too accurate we used Snapchat maps instead). Dissapointing, but a fun project nonetheless.

Please use my code if you're developing something for Life360, I've had absolutely no luck with the existing APIs online. (Click here)[https://github.com/reecepounder/life360-proximity-alert].

