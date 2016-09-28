---
bg: "IMGP8137.jpg"
layout: page
permalink: /blog/
title: "Blog"
crawlertitle: "Eric Cloninger's blog"
active: blog
---

<div>
{% for tag in site.tags %}{% assign t = tag | first %} <a class="blog-navigation" href="#{{ t | downcase }}">{{ t | capitalize }}</a> &middot;{% endfor %}
</div>

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

<h4 class="category-key" id="{{ t | downcase }}">{{ t | capitalize }}</h4>

<ul class="year">
  {% for post in posts %}
    {% if post.tags contains t %}
      <li>
        {% if post.lastmod %}
          <a href="{{ post.url }}">{{ post.title }}</a>
          <span class="date">{{ post.lastmod | date: "%d-%m-%Y"  }}</span>
        {% else %}
          <a href="{{ post.url }}">{{ post.title }}</a>
          <span class="date">{{ post.date | date: "%d-%m-%Y"  }}</span>
        {% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>


{% endfor %}
