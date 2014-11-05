---
layout: page
title: Teaching
---

Current classes
===

{% for post in site.posts %}
{% if post.category == "course"  and  post.current == true %}
{% include post-grid.html %}
<!-- [{{ post.title }}]({{ post.url | prepend: side.baseurl }}) -->
{% endif %}
{% endfor %}

Past classes
===

{% for post in site.posts %}
{% if post.category == "course"  and  post.current == false %}
[{{ post.title }}]({{ post.url | prepend: side.baseurl }})
{% endif %}
{% endfor %}
