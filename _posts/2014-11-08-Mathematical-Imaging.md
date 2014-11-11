---
layout: page
category: teaching
current: true
comments: false
title: Mathematical Imaging
---

Mathematical Imaging (or Image Processing) is a very broad field: it encompasses four main disciplines: *Image Compression*, *Edition/Restoration*, *Image Analysis*, and *Acquisition*.  Each of these disciplines are big fields on their own—for instance, within *Restoration* we have different problems (noise reduction, intensity adjustment, inpainting, sharpening, deblurring, correction of local distorsions…) and different techniques (based on PDEs, handling of coefficients in different frames, variational techniques, etc).  In the following pages we will explore some basic ideas and show some examples to illustrate how different branches of Mathematics can help you accomplish these tasks.

<div class="col-sm-8">
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
<div class="col-sm-4">
	<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=tf_til&ad_type=product_link&tracking_id=blancosilva-20&marketplace=amazon&region=US&placement=1439840458&asins=1439840458&linkId=FLHP4DLYSOTMF7XN&show_border=false&link_opens_in_new_window=true">
	</iframe>
	<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=tf_til&ad_type=product_link&tracking_id=blancosilva-20&marketplace=amazon&region=US&placement=0898712742&asins=0898712742&linkId=5SAE7JVTIDWJ4NCT&show_border=false&link_opens_in_new_window=true">
	</iframe>
</div>
