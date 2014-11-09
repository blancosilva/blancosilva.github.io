---
layout: page
title: Past Sections of MATH 122, MATH 141, MATH 142, MATH 241, and MATH 242
comments: false
category: page
current: false
---

{% for post in site.posts %}
{% if post.category == "course"  and  post.current == false %}
<li><a href="{{ post.url | prepend: side.baseurl }}">{{ post.title }}</a></li>
{% endif %}
{% endfor %}