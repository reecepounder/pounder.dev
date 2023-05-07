
---
layout: post
title: "SkillsUSA Florida Cybersecurity Competition"
subtitle: "Write-up and retrospective."
tags: ""
---

On April 20th, 2022, my teammate and I competed in the SkillsUSA Florida Cybersecurity competition against several other schools, high school and collegiate. We won first place, by a landslide - here's how.

#### Preperation
We were not told much, if anything, to prepare. We had no idea it would be a CTF style competition. In fact, the Florida chapter of SkillsUSA hadn't even published any materials on the subject. We instead relied on the National competition outline, which 

#### Competition
The competition was a super unique "hacker v hacker" CTF, in which we all had an identically vulnerable VM that we had to protect, and exploit everyone else's VM, to win. We were tasked with keeping several services (RPCBind and IRC) running on our machine, and stopping them on the other competitor's machines. We could also earn extra points by creating a write-up detailing what we tried, what we learned, and what the owners of the machines should do to improve security.

My teammate and I took a different approach from the other competitors in that we went on the defensive first. We actively seeked out the security issue in our system, and it wasn't long before we found one. Nmap had been set to run as root without needing a password (via sudo)
```
# /etc/sudoers

user ALL = (root) NOPASSWD: /usr/bin/nmap
```
If a malicious user had gained access, the nmap command could be used (via the --script option, using Lua) to run commands as root. There are no shortage of nmap reverse shell scripts online, and so we downloaded one for later use.

We also noticed the IRC software was severely out of date - enough that the RCE vulnerability it had was a module in metasploit. We wrote some firewall rules to block the other competitors' IP addresses from connecting to the IRC server, but not the scoreboard system that monitored whether it was up. Not that it mattered - because once that was done we got on exploiting those two vulnerabilites on other systems.

It wasn't long before the first other team fell. I felt bad, really - 30 minutes into the competition and they had no idea what had happened. Most everyone else assumed it was a technical issue, so we stayed silent - there were 4 hours left in the same room with these people. (Hey guys, if you're reading this, SORRY.)

After we got the hang of it, my teammate and I wrote an automated script to detect vulnerable machines on the network, gain RCE, elevate privileges and deliver a brutal blow that would render them bricked and require a judge to reset them (which took a very long time, for some reason. To this day, I have no idea why they couldn't simply restore point the VMs.) Our script blocked the web-based control panel they used to connect to the VM, blocked the ports for the two services, stopped and disabled the services, and then for good measure ran `rm -rf /`.

After about an hour all 7 or 8 teams were down, and just we were left. I couldn't help but record a little video as every competitor in the room put their hand up saying they were down. I cringe at it in retrospect, but in the moment we felt invincible.

Curiously, it seems like two teams got disqualified for trying to deauth the wifi network and thus preventing all competitors from doing anything. In theory it would've worked but we never saw any interruptions so I would suspect they didn't have the correct Wi-Fi cards. I think the judges only found out from the writeups - but in their defense the directions were "by any means necessary within the local network" and they did not clarify that "skills-cyber-wifi" was just a different SSID of the hotel wifi that everyone else was using.

#### Afterthoughts

The competition was executed horribly. It was not designed to rank contestants, like SkillsUSA does - it was a winner-takes-all luck based competition. While I had a lot of fun, it was not executed well at all - we weren't even told to bring our laptops. I think in the future they should seriously re-evaluate how they implement this competition and do a jeopardy-style CTF that can combine theoretical and technical knowledge in all areas of the SkillsUSA Technical Standards - thus making it true to it's word.

If you would like, you can read my writeup here: [click](https://pounder.dev/assets/SkillsUSA_Cybersecurity_Competition_Writeup_Redacted.pdf)

It isn't my best work, but it was the highest-scoring out of all submissions (according to an insider) and accurately reflects what you should do if faced with a similar competition style at this level. Hopefully, if you're reading this, you're planning to pursue this competition for yourself. I wish you good luck, and the best advice I can give you is to expect a competition completely unrelated to what you prepared for. Become an expert at Google-fu and learn a diverse skill range. And, don't be afraid to celebrate when you get the gold medal (but know that the Nationals one is about 2x larger - well worth the trip).

#### National Competition
I have not written a blog post for Nationals as it's hard for me to remember as of writing (May 2023). But if you want to email me about it my inbox is open. Find me on LinkedIn or other socials (though I probably won't accept you elsewhere) or guess my email address - it's not that hard.
