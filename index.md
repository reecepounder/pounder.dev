---
layout: default
---

## $: whoami
My name is Reece, and I'm a high school student currently studying cybersecurity. I am certified in the CompTIA trifecta, won the National Cyber Scholarship Competiton and Lockheed Martin Cyberquest last year, amongst other things, and am the president of a club at my school for which I am very passionate about.

## I write blog posts occasionally:
  <ul>
    {% for post in site.posts %}
      <li>
        <a href="{{ post.url }}"><b>{{ post.title }}</b> - {{post.subtitle}}</a>
      </li>
    {% endfor %}
  </ul>

