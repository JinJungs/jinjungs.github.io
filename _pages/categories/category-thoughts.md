---
title: "thoughts"
permalink: /categories/thoughts/
layout: archive
author_profile: true
taxonomy: thoughts
---

개발자로써 성장하기 위한 생각들을 기록합니다.

{% assign posts = site.categories.thoughts %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
