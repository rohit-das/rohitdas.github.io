---
layout: single
title: "Archery Journey"
---

Welcome to my archery log. This space is dedicated to my progression in barebow target shooting. This is a record of what I am learning and my experiences at various indoor and outdoor tournaments.

### Current Focus
*I am currently working on refining my stance alignment and building a highly consistent shot sequence for indoor competitive distances.*

***

### My Archery Adventure

<ul>
  {% for post in site.tags["barebow-archery"] %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>
