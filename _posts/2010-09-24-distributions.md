---
layout: page
title: Introduction to the Theory of Distributions
date: 2010-09-24 17:35:09.000000000 -04:00
category: teaching
comments: true
current: true
description: Distributions
---

The purpose of this course if to give a straightforward introduction to the Theory of Distributions, showing enough material to be able to understand the concept of *Fundamental Solutions of Differential Operators*, and the *Calculus of Wavefront Sets*.  I will be following mostly Lars Hörmander's"* **The Analysis of Linear Partial Differential Operators***" and Friedlander–Joshi's "***Introduction to the Theory of Distributions***".

Rather than adopting a formal class structure, I have planned different short readings exploring useful concepts, technical details about the objects studied, and presenting somewhat detailed constructions and examples.  Although initially not connected, this collection of readings will lead naturally to the two research topics mentioned before.

Suggestions and comments are very welcomed.  I hope you have the same pleasure reading these pages, as I experienced working on the subject.

<div class="row">
	<div class="col-sm-12">
		<div class="list-group">
			<a href="#" class="list-group-item active">Selected Lectures — Click on each title below for corresponding material</a>
			{% for post in site.posts %}
			{% if post.category == "course-material" and post.topic == "distributions" %}
			<a href="{{ post.url | prepend: side.baseurl }}" class="list-group-item">
				<h4 class="list-group-item-heading">{{ post.title }}</h4>
			</a>
			{% endif %}
			{% endfor %}
		</div>
	</div>
</div>
