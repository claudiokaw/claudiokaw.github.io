---
layout: single
title: "Tutorials"
permalink: /tutorials/
author_profile: true
classes: wide
---

Hands-on walkthroughs on AI, machine learning, and the algorithms behind them.

<div class="entries-list">
{% assign tutorials = site.posts | where_exp: "p", "p.categories contains 'tutorials'" %}
{% for post in tutorials %}
  <div class="archive__item" style="margin-bottom:1.5em;">
    <h2 class="archive__item-title" style="margin-top:0;">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>
    <p class="page__meta" style="color:#888;font-size:.8em;">{{ post.date | date: "%B %-d, %Y" }} · {% include read-time.html %}</p>
    <p class="archive__item-excerpt">{{ post.excerpt | strip_html | truncatewords: 40 }}</p>
  </div>
{% endfor %}
</div>
