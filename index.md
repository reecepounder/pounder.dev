---
layout: default
---

## whoami
My name is Reece, and I'm a high school student currently studying cybersecurity. I am certified in the CompTIA trifecta, won the National Cyber Scholarship Competiton and Lockheed Martin Cyberquest last year, amongst other things, and am the president of a club at my school for which I am very passionate about.

## stuff
Some of the stuff I've done over the years:
- ran a cybersecurity club at my school [(visit)](https://cbcybersec.com)
- won a lockheed martin cyberquest [(proof)](https://www.lockheedmartin.com/en-us/who-we-are/communities/cyber-quest/cyber-quest-winners/cyber-quest-2021-winners.html)
- won the national cyber scholarship competition [(proof)](https://www.nationalcyberscholarship.org/winners-2021)
- some other stuff i have to put later

## blog
  <ul>
    {% for post in site.posts %}
      <li>
        <a href="{{ post.url }}"><b>{{ post.title }}</b> - {{post.subtitle}}</a>
      </li>
    {% endfor %}
  </ul>

