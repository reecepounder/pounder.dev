---
layout: default
---

## whoami
Hi, I'm Reece - an IT nerd and cybersecurity student. I am working on my degree and my dream job is to work on a red team. I currently have an A.S., but my goal is to pursue an M.S. or beyond.

## accomplishments
I have had my fair share of adventures:
- I beta-tested the CySA+ CS0-003 exam for CompTIA
- I built temporary networking for 300+ clients for a conference by HP
- I used to work teaching kids to code
- I ran a cybersecurity club at my high school (we got 50+ students CompTIA / MTA certified)
- My team won Lockheed-Martin's CyberQuest CTF [(proof)](https://www.lockheedmartin.com/en-us/who-we-are/communities/cyber-quest/cyber-quest-winners/cyber-quest-2021-winners.html)
- I won the National Cyber Scholarship twice [(2021)](https://www.nationalcyberscholarship.org/winners-2021), [(2022)](https://www.nationalcyberscholarship.org/winners-2022),
- I won the SkillsUSA National Cybersecuity Competition [(proof)](https://youtu.be/-7fZTGrj2xc?t=6551)

## blog
My blog posts are intermittent and of questionable quality, but I hope they teach you something new!
  <ul>
    {% for post in site.posts %}
        <li>
          <a href="{{ post.url }}"><b>{{ post.title }}</b> - {{post.subtitle}}</a>
        </li>
    {% endfor %}

  </ul>

