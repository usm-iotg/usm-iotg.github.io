---
layout: page
title: USM-IoT
tagline: (Internet of Things)
---
{% include JB/setup %}

## USM-Galileo Curriculum Contents

### *Latest*

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>



