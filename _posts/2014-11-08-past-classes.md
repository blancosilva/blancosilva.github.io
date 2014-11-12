---
layout: page
title: Past Sections of Undergraduate Calculus
comments: false
category: teaching
---

Click on each title to retrieve corresponding syllabus and lesson plans

<div class="row">
	<div class="col-sm-6">
		<div class="list-group">
			<a href="#" class="list-group-item active">Freshman Calculus</a>
			{% for post in site.posts %}
			{% if post.category == "course"  and  post.current == false % and (post.description == "Calculus I" or post.description contains "Applied") %}
			<a href="{{ post.url | prepend: side.baseurl }}#" class="list-group-item">
				<h4 class="list-group-item-heading">{{ post.title }}</h4>
				<p class="list-group-item-text">{{ post.description }}</p>
			</a>
			{% endif %}
			{% endfor %}
		</div>
	</div>
	<div class="col-sm-6">
		<div class="list-group">
			<a href="#" class="list-group-item active">Intermediate Undergraduate classes</a>
			{% for post in site.posts %}
			{% if post.category == "course"  and  post.current == false % and (post.description == "Vector Calculus" or post.description contains "Equations" or post.description contains "II") %}
			<a href="{{ post.url | prepend: side.baseurl }}#" class="list-group-item">
				<h4 class="list-group-item-heading">{{ post.title }}</h4>
				<p class="list-group-item-text">{{ post.description }}</p>
			</a>
			{% endif %}
			{% endfor %}
		</div>
	</div>
</div>
