---
layout: default
title: Categories
permalink: /categories
---

{% for category in site.categories %}
  {% capture category_name %}{{ category | first }}{% endcapture %}
  <h2>{{category_name}}</h2>
  <ul>
    {% for posts in category %}
      {% for post in posts %}
        {% if post.url %}
          <li><a href="{{ post.url }}"> {{ post.title }} </a></li>
        {% endif %}
      {% endfor %}
    {% endfor %}
</ul>
{% endfor %}
