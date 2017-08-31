---
layout: page
title: 
---

  {% for post in site.posts %}

  <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>

  <div class="entry">
    {{ post.excerpt | remove: '<p>' | remove: '</p>' }}
  </div>

  {% endfor %}