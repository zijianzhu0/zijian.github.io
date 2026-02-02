---
layout: default
title: Photos
---

# Photos

{% assign photos = site.categories.photos | sort: "date" | reverse %}
{% for p in photos %}
- [{{ p.title }} ({{ p.year }})]({{ p.url }})
{% endfor %}