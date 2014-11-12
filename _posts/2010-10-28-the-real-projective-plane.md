---
layout: page
title: The Real Projective Plane
category: course-material
comments: true
topic: topology
---

Consider in the sphere <span>\\( \mathbb{S}_2 \subset \mathbb{R}^3, \\)</span> the relation induced by identification of antipodal points; that is, given <span>\\( z_1, z_2 \in \mathbb{S}_2 \\)</span>, set <span>\\( z_1 \sim z_2 \\)</span> if and only <span>\\( z_1 = \pm z_1. \\)</span>  The corresponding quotient space <span>\\( \mathbb{P} = \big( \mathbb{S}_2 / \sim \big) \\)</span> is what we call <strong>real projective space.</strong>

Since we are interested in the topological properties of this space, we actually define a real projective space to be any homeomorphic set to <span>\\( \mathbb{P}. \\)</span>  Among those, we are interested in one that can be realized from a square, by identification of its sides (in a similar manner as we did with the <a href="http://blancosilva.github.io/course-material/2010/10/28/torus.html" target="_self">torus</a>).  We proceed as follows:

Assume that we start from the unit sphere <span>\\( \\{ (x_1,x_2,x_3) \in \mathbb{R}^3 : x_1^2+x_2^2+x_3^2=1 \\} \\)</span>, and note that the upper hemisphere <span>\\( H=\\{ (x_1,x_2,x_3) \in \mathbb{R}^3 : x_1^2+x_2^2+x_3^2=1, x_3 \geq 0  \\} \\)</span> contains at least one of each pair of antipodal points.  If both antipodal points occur in <span>\\( H \\)</span>, they will necessarily lie over the circle <span>\\( \\{ (x_1, x_2, 0) \in \mathbb{R}^3 : x_1^2+x_2^2=1 \\}. \\)</span>  The hemisphere <span>\\( H \\)</span> is obviously homeomorphic to a disk (by a simple vertical projection onto the plane <span>\\( \\{x_3=0 \\}, \\)</span> for example).  And <a href="http://blancosilva.github.io/course-material/2010/10/27/homeomorphisms.html" target="_self">the disk is homeomorphic to a square</a>, so we may use a composition of both to realize a homomorphism from <span>\\( H \\)</span> to <span>\\( \square_2. \\)</span>

Define in <span>\\( H \\)</span> an equivalence relation that identifies two antipodal points on the border, and notice that the homeomorphism just computed takes that identification to the following: Given <span>\\( (x_1,x_2), (y_1,y_2) \in \square_2 \\)</span>, it is <span>\\( (x_1,x_2) \sim (y_,y_2) \\)</span> if

* <span>\\( x_1=y_1 \\)</span> and <span>\\( x_2=y_2 \\)</span>, or
* <span>\\( x_1y_1 = -1 \\)</span> and  <span>\\( x_2=1-y_2 \\)</span>, or
* <span>\\( x_2y_2=-1 \\)</span> and <span>\\( x_1=1-y_1 \\)</span>.

A diagram representing the quotient space <span>\\( \big( \square_2 / \sim \big) \\)</span> is presented below:

<table style="width:50%;margin-right:auto;margin-left:auto;border-width:0;">
<tbody>
<tr>
<td style="width:100%;text-align:center;vertical-align:middle;border-width:0;" colspan="2"><img src="http://farm2.static.flickr.com/1352/5124398882_1bfac0cf77_o_d.jpg" alt="" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;vertical-align:middle;border-width:0;padding:0;"><img src="http://farm2.static.flickr.com/1097/5123795475_95c3b86753_o_d.jpg" alt="" /></td>
<td style="width:50%;text-align:center;vertical-align:middle;border-width:0;padding:0;"><img src="http://farm5.static.flickr.com/4008/5124399028_810a059e36_o_d.jpg" alt="" /></td>
</tr>
</tbody>
</table>

The punch-line is, of course, to construct a homeomorphism from the real projective plane <span>\\( \mathbb{P} \\)</span> as defined above, to the quotient space <span>\\( \big( \square_2 / \sim \big). \\)</span>  The reader should not have much trouble to give an analytic expression of such a map following the steps above.
