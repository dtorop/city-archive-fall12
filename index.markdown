---
layout: base
title: Main Page
---

CCNY DIAP, Fall 2012
-------

### Class technical notes

{% for post in site.posts %}
<p>{{ post.date | date: "%Y-%m-%d" }} - <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
{% if post.abstract %}
: <i> {{ post.abstract }} </i>
{% endif %}
</p>
{% endfor %}
