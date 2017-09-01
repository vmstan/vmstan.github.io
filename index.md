---
layout: default
---

{% for post in site.posts %}

      {% if post.external_url %}

      <h3><a href="{{ post.external_url }}">{{ post.title }}</a> via {{ post.host }} &#8594;</h3>
      <p>{{ post.lead }}</p>

      {% else %}

      <h3><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: '%b %-d, %Y'}}</time></h3>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        <p>{{ post.lead }}</p>

      {% endif %}
 
{% endfor %}
