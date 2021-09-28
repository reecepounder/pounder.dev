---
layout: default
---

<div class="posts">
  {% for post in site.posts %} 
      
      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>
        {{ post.content | truncatewords:40}}
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>

  {% endfor %}
</div>
