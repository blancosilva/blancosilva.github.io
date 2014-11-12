---
layout: page
title: An Introduction to Algebraic Topology
date: 2010-10-27 15:06:59.000000000 -04:00
category: teaching
current: false
description: Algebraic Topology
comments: false
---

For any topological space <span>\\( X \\)</span> and any point <span>\\( x_0 \in X, \\)</span> we aim to define a group <span>\\( \pi(X,x_0) \\)</span>, the Fundamental Group of <span>\\( X \\)</span>, by a simple and intuitive manner by manipulation of closed paths in the space.  It will be proven that this group is the same for any choice of point <span>\\( x_0 \\)</span>, and also that the group is an invariant of the topological space <span>\\( X \\)</span>—meaning, that any other space <span>\\( Y \\)</span> homeomorphic to <span>\\( X \\)</span> must have the same group.

This helps us construct a solid theory where (some) topological properties are turned into algebraic properties of the corresponding groups, hence establishing some sort of dictionary between different mathematical languages. This is the basic strategy of Algebraic Topology.

<div class="row">
	<div class="col-sm-12">
		<div class="list-group">
			<a href="#" class="list-group-item active">Selected Lectures — Click on each title below for corresponding material</a>
			{% for post in site.posts %}
			{% if post.category == "course-material" and post.topic == "topology" %}
			<a href="{{ post.url | prepend: side.baseurl }}" class="list-group-item">
				<h4 class="list-group-item-heading">{{ post.title }}</h4>
			</a>
			{% endif %}
			{% endfor %}
		</div>
	</div>
</div>
