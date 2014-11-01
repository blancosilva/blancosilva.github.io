---
layout: page
title: Teaching
---

{% for category in site.data.teaching %}
 * {{ category.description }}
	{% for course in category.courses %}
	[{{ course.name }}]	({{ category.folder | prepend: site.baseurl }}{{ course.url }})
	{% endfor %}
{% endfor %} 
