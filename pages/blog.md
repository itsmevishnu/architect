---
layout: default
title: Blogs
permalink: /blogs
---

{% for post in site.posts%}

## [{{ post.title}}]({{ post.url }})

  {{ post.excerpt }}
{% endfor%}
