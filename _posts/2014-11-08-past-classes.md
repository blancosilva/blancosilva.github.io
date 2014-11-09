---
layout: page
title: Past Sections of Undergraduate Calculus
comments: false
category: teaching
---

<div class="alert alert-success" role="alert">
	Click on each course to retrieve corresponding syllabus and lesson plan.
</div>

<div class="col-sm-8">
	<div class="list-group">
		{% for post in site.posts %}
		{% if post.category == "course"  and  post.current == false %}
		<a href="{{ post.url | prepend: side.baseurl }}#" class="list-group-item">
			<h4 class="list-group-item-heading">{{ post.title }}</h4>
			<p class="list-group-item-text">{{ post.description }}</p>
		</a>
		{% endif %}
		{% endfor %}
	</div>
</div>
