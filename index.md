---
layout: page
title: 我的随笔
tagline: Supporting tagline
---
{% include JB/setup %}

<div class="blog-index">
  {% assign post = site.posts.first %}
  {% assign content = post.content %}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

</div>
