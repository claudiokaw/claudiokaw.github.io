---
layout: single
title: "Projects"
permalink: /projects/
author_profile: true
classes: wide
---

A selection of research explorations and applied work. Each project links to a
detail page — replace or expand these as your work evolves.

<div class="entries-list">
{% assign sorted_projects = site.projects | sort: "date" | reverse %}
{% for project in sorted_projects %}
  <div class="archive__item" style="margin-bottom:1.5em;">
    <h2 class="archive__item-title" style="margin-top:0;">
      <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
    </h2>
    {% if project.tags %}<p style="color:#888;font-size:.8em;">{{ project.tags | join: " · " }}</p>{% endif %}
    <p class="archive__item-excerpt">{{ project.excerpt }}</p>
  </div>
{% endfor %}
</div>
