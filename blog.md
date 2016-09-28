---
bg: "IMGP8137.jpg"
layout: page
permalink: /blog/
title: "Blog"
crawlertitle: "Eric Cloninger's blog"
active: blog
---

{% for post in site.posts  %}
{% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
{% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}

{% if forloop.first %}
<h2 id="{{ this_year }}-ref">{{this_year}}</h2>
<ul class="year">
{% endif %}

<li><a href="{{ post.url }}">{{ post.title }}</a><span class="date">
:{% for tag in post.tags %}
{{ tag }} :
{% endfor %}

</span></li>

{% if forloop.last %}
</ul>
{% else %}

{% if this_year != next_year %}
</ul>
<h2 id="{{ next_year }}-ref">{{next_year}}</h2>
<ul class="year">
{% endif %}

{% endif %}

{% endfor %}
