---
layout: default
title: 카테고리
permalink: /categories/
---

<div class="wrap">
  <h1 class="page-title">카테고리</h1>
  <div class="grid">
  {% for pair in site.categories %}
    {% assign cname = pair[0] %}
    {% assign posts_in_cat = pair[1] %}
    {% if posts_in_cat and posts_in_cat.size > 0 %}
      {% assign posts_sorted = posts_in_cat | sort: "date" | reverse %}
      {% capture cat_slug %}{{ cname | slugify }}{% endcapture %}
      <div>
        <div class="section-head">
          <h2>{{ cname }}</h2>
          <a href="{{ '/category/' | append: cat_slug | append: '/' | relative_url }}">더 보기</a>
        </div>
        <div class="cards">
          {% for p in posts_sorted limit:4 %}
          <a class="card" href="{{ p.url | relative_url }}">
            {% if p.image %}<div class="thumb" style="background-image:url('{{ p.image | relative_url }}');"></div>{% endif %}
            <div class="meta">
              <div class="cat">{{ cname }}</div>
              <h3 class="title">{{ p.title }}</h3>
              {% if p.description %}<p class="desc">{{ p.description }}</p>{% endif %}
              <div class="date">{{ p.date | date: "%Y-%m-%d" }}</div>
            </div>
          </a>
          {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
  </div>
</div>
