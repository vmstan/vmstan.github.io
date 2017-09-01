---
layout: default
---

{% for post in site.posts %}
<p>
      {% if post.external_url %}
      <h3>→ {{ post.host }}</h3>
      {% else %}
      <h3><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: '%b %-d, %Y'}}</time></h3>
      {{ post.lead }}
      {% endif %}
    <h2><a href="{% if post.external_url %}{{ post.external_url }}{% else %}{{ post.url }}{% endif %}">
      {{ post.title }}
    </a></h2>
    {{ post.lead }}
 </p>
{% endfor %}
