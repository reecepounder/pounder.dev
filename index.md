---
layout: default
---

## whoami
Hi, I'm Reece - a passionate cybersecurity student. I am pursuing my degree and hope to some day work on a red team, working with both physical and digital penetration testing.

## accomplishments
I have had my fair share of adventures:
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

