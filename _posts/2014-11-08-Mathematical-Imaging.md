---
layout: page
category: teaching
current: true
comments: false
title: Mathematical Imaging
---

Mathematical Imaging (or Image Processing) is a very broad field: it encompasses four main disciplines: *Image Compression*, *Edition/Restoration*, *Image Analysis*, and *Acquisition*.  Each of these disciplines are big fields on their own—for instance, within *Restoration* we have different problems (noise reduction, intensity adjustment, inpainting, sharpening, deblurring, correction of local distorsions…) and different techniques (based on PDEs, handling of coefficients in different frames, variational techniques, etc).  In the following pages we will explore some basic ideas and show some examples to illustrate how different branches of Mathematics can help you accomplish these tasks.

<div class="row">
<div class="col-sm-12">
	<div class="list-group">
		<a href="#" class="list-group-item active">Selected Lectures — Click on each title below for corresponding material</a>
		{% for post in site.posts %}
		{% if post.category == "course-material" and post.topic == "imaging" %}
		<a href="{{ post.url | prepend: side.baseurl }}" class="list-group-item">
			<h4 class="list-group-item-heading">{{ post.title }}</h4>
		</a>
		{% endif %}
		{% endfor %}
	</div>
</div>
</div>
