---
layout: post
title: Convex triangle-square polygons
date: 2010-10-20 09:38:57.000000000 -04:00
category: post
comments: true
image:
  teaser: https://i0.wp.com/farm2.static.flickr.com/1316/5101252276_83447d2752_o_d.jpg 
---
<div class="well">
	<p>
		Consider an infinite supply of cardboard equilateral triangles and squares, all of them with side length of one inch.  With these pieces, we desire to form convex polygons of different sides.  It is trivial to come up with this kind of polygons for sides 3, 4, 5 and 6.
	</p>
	<ul>
		<li>Construct examples of these convex polygons for sides 7, 8, 9 and 10.</li>
		<li>Can you construct an 11-side convex polygon with these pieces?</li>
		<li>What would be the convex polygon with the largest number of sides that you could construct with these pieces?</li>
	</ul>
</div>

<p style="text-align:center;"><img src="https://i0.wp.com/farm2.static.flickr.com/1316/5101252276_83447d2752_o_d.jpg" alt="" style="width:75%" /></p>

Before we go ahead and construct the polygons, let us try to find as much information as possible:

* The interior angles of a polygon with <span>\\( n \\)</span> sides add up to <span>\\( 180n - 360 \\)</span>.
* By construction, all the convex angles at the exterior vertices of the planar graphs can only be one of the following: <span>\\( 60^\circ, 90^\circ, 120^\circ \\)</span>, and <span>\\( 150^\circ \\)</span>. Although technically possible, we should not count the flat angle <span>\\( 180^\circ \\)</span>, since the occurrence of such angle indicates the presence of an "extended edge."If we have <span>\\( a \\)</span>, <span>\\( b \\)</span> and <span>\\( c \\)</span> interior angles of respectively <span>\\( 60^\circ \\)</span>, <span>\\( 90^\circ \\)</span> and <span>\\( 120^\circ \\)</span> at the exterior vertices of the polygon, and of course <span>\\( n-a-b-c \\)</span> interior angles of <span>\\( 150^\circ \\)</span> at the same vertices, then it must be
    <div>
    	\begin{equation}
    	60a + 90b + 120c + 150(n-a-b-c) = 180n - 360,
    	\end{equation}
    </div>
which reduces to
    <div>
    	\begin{equation}
    	3a + 2b + c + n = 12.
    	\end{equation}
    </div>
This is a very strong statement!  It indicates, among other things, that **such polygons cannot have more than 12 sides!** This answers the third question of our puzzle.
Incidentally, it will also help us find examples of constructions.  For example, for the seven-sided polygon, a choice of angles that works for me is <span>\\( a=0 \\)</span>, <span>\\( b=2 \\)</span> and <span>\\( c=1 \\)</span> (that is: no <span>\\( 60^\circ \\)</span> angles, two right angles, only one angle of <span>\\( 120^\circ \\)</span> and four angles of <span>\\( 150^\circ \\)</span>.
For the case <span>\\( n=11 \\)</span>, there is only one possibility: <span>\\( a=0 \\)</span>, <span>\\( b=0 \\)</span>, <span>\\( c=1 \\)</span>; that is, only one angle of <span>\\( 120^\circ \\)</span>, and ten angles of <span>\\( 150^\circ \\)</span>.  Will this allow us to construct the 11-sided convex polygon?  The answer is **yes**, but to come up with an example, you may need to make use of some <span>\\( 180^\circ \\)</span> angles.
I have included a list with a set of choices of angles, for polygons of sides <span>\\( n=7,8,9,10,11,12 \\)</span> for which I was able to find a valid construction:
<table class="table table-bordered">
<tbody>
<tr>
<td>\( n \)</td>
<td>\( 60^\circ \)-angles</td>
<td>\( 90^\circ \)-angles</td>
<td>\( 120^\circ \)-angles</td>
<td>\( 150^\circ \)-angles</td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:2px;">Planar graph</td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;">7</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">2</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">1</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">4</td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:1px;"><img src="https://i0.wp.com/farm2.static.flickr.com/1436/5102420388_b99423099e_o_d.jpg" alt="" /></td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;">8</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">4</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">4</td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:1px;"></td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;">9</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">3</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">6</td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:1px;"></td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;">10</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">2</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">8</td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:1px;"></td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;">11</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">1</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">10</td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:1px;"></td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;">12</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">0</td>
<td style="text-align:center;vertical-align:middle;border-width:1px;">12</td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:1px;"></td>
</tr>
</tbody>
</table>
Feel free to construct the corresponding polygons, and fill in the table.

<hr />

### Miscellaneous

Although not strictly necessary, at some point during the exploration of this problem I used other facts about planar graphs that came in handy to help construct my examples.  The most notable of those appear below:

* Each <span>\\( n \\)</span>-sided convex polygon that we construct by putting together these triangles and squares form a planar graph with <span>\\( V \\)</span> vertices <span>\\( (V \geq n) \\)</span>, <span>\\( E \\)</span> edges <span>\\( (E \geq n) \\)</span> and <span>\\( F \\)</span> faces <span>\\( (F \geq 1) \\)</span>.  These planar graphs all have Euler characteristic 1, and thus <span>\\( V - E + F =1 \\)</span>.
* Assume we are able to construct a <span>\\( n \\)</span>-sided polygon by using <span>\\( x \\)</span> triangles (according to the statement above, there should be <span>\\( F-x \\)</span> squares). By adding all the involved angles, we obtain
    <div>
    	\begin{equation}
    	\underbrace{3 \cdot 60 \cdot x}_{\text{triangles}} + \underbrace{4 \cdot 90 \cdot (F-x)}_{\text{squares}} = \underbrace{180n - 360}_{\text{polygon}} + \underbrace{360 (V-n)}_{\text{interior vertices}},
    	\end{equation}
    </div>
which reduces to
    <div>
    	\begin{equation}
    	n - x = 2(V-1-F).
    	\end{equation}
    </div>
In particular, this indicates that <span>\\( x \\)</span> and <span>\\( n \\)</span> have the same parity.
