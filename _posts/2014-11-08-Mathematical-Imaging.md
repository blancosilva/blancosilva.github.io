---
layout: page
category: course
current: true
comments: false
title: Mathematical Imaging
---

Mathematical Imaging (or Image Processing) is a very broad field: it encompasses three main disciplines: *Image Compression*, *Restoration* and *Image Analysis*.  Each of these disciplines are big fields on their own—for instance, within *Restoration* we have different problems (noise reduction, intensity adjustment, inpainting, sharpening, deblurring, correction of local distorsions…) and different techniques (based on PDEs, handling of coefficients in different frames, variational techniques, etc).  In the following pages we will explore some basic ideas and show some examples to illustrate how different branches of Mathematics can help you accomplish these tasks.

<p style="text-align:center;">
	<a href="http://www.amazon.com/gp/product/1439840458/ref=as_li_tf_il?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399373&amp;creativeASIN=1439840458"><img border="0" src="http://ws.assoc-amazon.com/widgets/q?_encoding=UTF8&amp;Format=_SL160_&amp;ASIN=1439840458&amp;MarketPlace=US&amp;ID=AsinImage&amp;WS=1&amp;tag=blancosilva-20&amp;ServiceVersion=20070822"></a><img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=1439840458&amp;camp=217145&amp;creative=399373" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" /><br /><a href="http://www.amazon.com/gp/product/1439840458/ref=as_li_tf_tl?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399373&amp;creativeASIN=1439840458">The Image Processing Handbook, Sixth Edition</a><img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=1439840458&amp;camp=217145&amp;creative=399373" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" />
</p>

<div class="col-sm-8">
	<div class="list-group">
		{% for post in site.posts %}
		{% if post.category == "course-material" and post.topic == "imaging" %}
		<a href="{{ post.url | prepend: side.baseurl }}" class="list-group-item">
			<h4 class="list-group-item-heading">{{ post.title }}</h4>
		</a>
		{% endif %}
		{% endfor %}
	</div>
</div>
