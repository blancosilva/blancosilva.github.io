---
layout: post
title: A geometric fallacy
date: 2010-10-14 09:15:12.000000000 -04:00
category: post
comments: true
image:
  teaser: http://farm5.static.flickr.com/4041/5081312425_6ebb5b2376_o_d.jpg
---

A geometric fallacy is basically a geometric construction that leads to a false result.  I once found an obscure russian treatise on this matter (published by мир), that kept me entertained for weeks: Ya.S.Dubnov's *Errores en las demostraciones geométricas*.  The edition I have is a decent translation into Spanish, made by K.Medkov in 1993, although unfortunately some of the translated statements had to be treated with a grain of salt.  Nonetheless, I did enjoy greatly browsing through the different geometric problems, and learned quite a bit about mathematical reasoning.

Most of the geometric fallacies rely on the use of correct reasoning on the incorrect figures. But I would like to present here one of the most amusing ones, not only for the fact that it didn't use a wrong figure, but also because it takes us to deliver a contradiction to the Pythagorean Theorem!  It goes like this:

> In all right triangles, the sum of the lengths of the legs equals the length of the hypothenuse.  That is, the sides \\( a \\), \\( b \\) and \\( c \\) satisfy \\( a+b=c \\), where the largest side is conventionally denoted \\( c \\) and is called the hypotenuse.  The other two sides, of length \\( a \\) and \\( b \\) are called the legs (or the catheti)
>
> (see the page in e.g. <a href="http://en.wikipedia.org/wiki/Triangle" target="_blank">wikipedia</a> for more information about triangles)

The "proof" of this absurd result is done by taking to the limit a clever construction.  Let us start with a given right triangle, and consider its two legs alone:

<table style="width:100%;padding:10px;">
<tbody>
<tr>
<td style="text-align:center;width:50%;padding:10px;"><img src="http://farm5.static.flickr.com/4111/5081178557_40b8064807_o_d.jpg" alt="" width="100%" /></td>
<td style="text-align:center;width:50%;padding:10px;"><img src="http://farm5.static.flickr.com/4070/5081178429_4d25461f8c_o_d.jpg" alt="" width="100%" /></td>
</tr>
</tbody>
</table>

Starting in the vertex <span>\\( A \\)</span>, consider a staircase of segments that goes through the midpoints of the sides of the triangle, until reaching the vertex <span>\\( B \\)</span>.  Notice that the lengths of segments of this staircase add up to <span>\\( a+b \\)</span> by construction.

<table style="width:100%;padding:10px;">
<tbody>
<tr>
<td style="text-align:center;width:50%;padding:10px;"><img src="http://farm5.static.flickr.com/4049/5081772098_cb597f38dd_o_d.jpg" alt="" width="100%" /></td>
<td style="text-align:center;width:50%;padding:10px;"><img src="http://farm5.static.flickr.com/4109/5081178511_b69753aa14_o_d.jpg" alt="" width="100%" /></td>
</tr>
</tbody>
</table>

Repeat the same staircase construction starting in the vertex <span>\\( A \\)</span>, and using the midpoints of the previous staircase, until reaching vertex <span>\\( B \\)</span>.  The lengths of the segments of this new staircase still add up to <span>\\( a+b \\)</span>.

<table style="width:100%;padding:10px;">
<tbody>
<tr>
<td style="text-align:center;width:50%;padding:10px;"><img src="http://farm5.static.flickr.com/4041/5081312425_6ebb5b2376_o_d.jpg" alt="" width="100%" /></td>
<td style="text-align:center;width:50%;padding:10px;"><img src="http://farm5.static.flickr.com/4028/5081312385_61fb35a7df_o_d.jpg" alt="" width="100%" /></td>
</tr>
</tbody>
</table>

By taking this construction to the limit, new staircases of length <span>\\( a+b \\)</span> are constructed that tend to the hypotenuse (in the sense that, after some iterations, the staircase and the hypotenuse will be *as close to each other* as desired).  We infere that the limit of these staircases is indeed the hypotenuse, and since the length of each staircase remained constant <span>\\( a+b \\)</span>, the length of the hypotenuse must also be <span>\\( a+b \\)</span>.

<p style="text-align:right;"><strong>QED</strong></p>

This is obviously not true. **What is wrong with this proof?**
