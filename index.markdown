---
layout: base
title: Main Page
---

Classes
-------

{% for post in site.posts %}
<p>{{ post.date | date: "%Y-%m-%d" }} - <a href="{{ post.url }}">{{ post.title }}</a>
{% if post.abstract %}
: <i> {{ post.abstract }} </i>
{% endif %}
</p>
{% endfor %}
