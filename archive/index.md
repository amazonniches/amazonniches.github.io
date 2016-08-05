---
layout: post
title: Archives
skip_related: true
---

{% assign totalwords = 0 %}
{% for post in site.posts %}
  {% assign wordcount = post.content | number_of_words %}
  {% assign totalwords = totalwords | plus: wordcount %}
{% endfor %}

Archive of our entire site. All posts totalling {{ totalwords }} arranged in chronological order. Includes reviews, news, and random quirks.

<div id="archive">
{% for post in site.posts %}
  {% assign currentdate = post.date | date: "%Y" %}
  {% if currentdate != date %}
    {% unless forloop.first %}</ul>{% endunless %}
<h2>{{ currentdate }}</h2>
<ul>
    {% assign date = currentdate %}
  {% endif %}
  <li {% if post.favorite %}class="favorite"{% endif %}>
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
  {% if forloop.last %}</ul>{% endif %}
{% endfor %}
</div>


