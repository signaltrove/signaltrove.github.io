---
layout: default
title: Home
---

{% for post in site.posts %}
<article class="post-card">
  {% if post.image %}
    <a href="{{ post.url | relative_url }}">
      <img class="thumb" src="{{ post.image | relative_url }}" alt="{{ post.title }}">
    </a>
  {% endif %}
  <h2 style="margin:8px 0;"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
  <div class="meta">{{ post.date | date: "%Y-%m-%d" }}</div>
  <p>{{ post.description | default: post.excerpt | strip_html | truncate: 160 }}</p>
</article>
{% endfor %}
