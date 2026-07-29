---
layout: single
title: Life & Updates
---
[Home](/) | [About](/about) | [Travels](/travel) | [Hobbies & Projects](/projects) | [Life & Updates](/blog)

***

# Life & Updates

From dialing in our daily wellness routines to experimenting with new whole-food, plant-based meals in the Instant Pot and air fryer, here are our latest everyday updates.

### Recent Posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>
