---
layout: default
---

## Posts:
  <ul>
    {% for post in site.posts %}
      <li>
        <a href="{{ post.url }}"><b>{{ post.title }}</b> - {{post.subtitle}}</a>
      </li>
    {% endfor %}
  </ul>

