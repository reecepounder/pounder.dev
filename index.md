---
layout: default
---

## Posts:
  {% for post in site.posts %} 
      
      <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
        {{ post.content | truncatewords:40}}
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>

  {% endfor %}

