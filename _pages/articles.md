---
layout: single
title: "Articles"
permalink: /articles/
author_profile: true
classes: wide
---

Essays and notes on algorithms, payments, and the ideas I keep circling back to.

<div class="entries-list">
{% assign articles = site.posts | where_exp: "p", "p.categories contains 'articles'" %}
{% for post in articles %}
  <div class="archive__item" style="margin-bottom:1.5em;">
    <h2 class="archive__item-title" style="margin-top:0;">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>
    <p class="page__meta" style="color:#888;font-size:.8em;">{{ post.date | date: "%B %-d, %Y" }}</p>
    <p class="archive__item-excerpt">{{ post.excerpt | strip_html | truncatewords: 40 }}</p>
  </div>
{% endfor %}
</div>
