---
layout: default
---

{% for post in site.posts %}

{% if post.external_url %}

<h3><a href="{{ post.url }}">{{ post.title }}</a> via {{ post.host }} <a href="{{ post.external_url }}">&#8594;</a></h3>

{% else %}

<div class="date">{{ page.date | date: "%B %e, %Y" }}</div>
<h2><a href="{{ post.url }}">{{ post.title }}</a></h2>

{% endif %}

{% if post.lead %}
<div class="entry">{{ post.lead }}</div>
{% else %}
<div class="entry">{{ post.excerpt }}</div>
{% endif %}


<hr />
{% endfor %}