---
layout: default
---

## whoami
Hi, I'm Reece, and I'm a passionate cybersecurity enthusiast. I've just graduated high school with the CompTIA trifecta, and I've won several awards and competitions listed below. I sometimes post on my blog when something big happens - check it out :)

## stuff
Some of my accomplishments:
- i founded and led a cybersecurity club at my high school (we got 50+ students comptia/mta certified)
- won a lockheed martin cyberquest [(proof)](https://www.lockheedmartin.com/en-us/who-we-are/communities/cyber-quest/cyber-quest-winners/cyber-quest-2021-winners.html)
- won the national cyber scholarship competition twice [(2021)](https://www.nationalcyberscholarship.org/winners-2021), [(2022)](https://www.nationalcyberscholarship.org/winners-2022),
- became the skillsusa national cybersecurity champion [(proof)](https://youtu.be/-7fZTGrj2xc?t=6551)

## blog
  <ul>
    {% for post in site.posts %}
        <li>
          <a href="{{ post.url }}"><b>{{ post.title }}</b> - {{post.subtitle}}</a>
        </li>
    {% endfor %}

  </ul>

