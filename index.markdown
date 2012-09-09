---
layout: base
title: Main Page
---

City College - DIAP - Workshop: Medium, Fall 2012
-------

### Classes

{% for post in site.posts %}
<p>{{ post.date | date: "%Y-%m-%d" }} - <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
{% if post.abstract %}
: <i> {{ post.abstract }} </i>
{% endif %}
</p>
{% endfor %}
