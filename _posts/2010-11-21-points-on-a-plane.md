---
layout: page
title: Points on a plane
date: 2010-11-21 10:36:02.000000000 -05:00
category: post
comments: true
image:
  teaser: https://i0.wp.com/farm6.static.flickr.com/5161/5195162552_f8523866e3_o_d.jpg
---

A few puzzles about sets of points:

<div class="well">
Suppose \( S \) is a finite set of points on a plane, such that for any two points \( A,B \in S \), there is a third point \( D \in S \), collinear with \( A \) and \( B \) (and different from \( A \) and \( B \)).

<strong>Show that all points of \( \boldsymbol{S} \) are collinear.</strong>
</div>

The nicest solution I know of this problem comes by *reductio ad absurdum*, and goes like this:

Suppose that not all points in <span>\\( S \\)</span> are collinear.  Among all possible triangles that we can form using points from this set as vertices, chose the one with the smallest height, say <span>\\( \delta \\)</span>; label the vertices at the base of the triangle <span>\\( A \\)</span> and <span>\\( B \\)</span>, and the remaining vertex <span>\\( C. \\)</span>  It will not be hard for the reader to realize that this implies, in particular, that the projection of <span>\\( C \\)</span> on the line from <span>\\( A \\)</span> and <span>\\( B \\)</span> is either one of the previous two vertices, or it is located inside of the segment that joins them.

By hypothesis, there is a third point <span>\\( D \\)</span> which is collinear with <span>\\( A \\)</span> and <span>\\( B \\)</span>.  Consider now the new triangles that arose: <span>\\( \triangle ADC, \triangle BDC. \\)</span>  The trick now is to realize that the smallest of the heights of one of these two triangles, say <span>\\( \delta', \\)</span> is necessarily smaller than <span>\\( \delta \\)</span>.  This is a contradiction!

<p style="text-align:center;"><img src="https://i0.wp.com/farm6.static.flickr.com/5161/5195162552_f8523866e3_o_d.jpg" width="100%" />

<hr />

The second puzzle was sent by <a href="http://www.math.sc.edu/~howard/">Ralph Howard</a>:

<div class="well">
Let \( S \) be a infinite set of points on a plane, such that the distance between any two is an integer.

<strong>Prove that all points in \( \boldsymbol{S} \) are collinear.</strong>
</div>

Ralph pointed up to a clever solution to this riddle by Paul Erdös.  He published it in a short article, titled *Integral distances*, published in Bull. Amer. Math. Soc. 51, (1945). 996.  It goes as follows:

Suppose you have three points <span>\\( A \\)</span>, <span>\\( B \\)</span> and <span>\\( C \\)</span> with integer distances between them and not all on the same line. Let us denote <span>\\( \mathop{d}(A,B) \\)</span> the distance between points <span>\\( A \\)</span> and <span>\\( B \\)</span>.  If <span>\\( \mathop{d}(A,Q) \\)</span> and <span>\\( \mathop{d}(B,Q) \\)</span> are both integers, note that <span>\\( \mathop{d}(A,Q) - \mathop{d}(B,Q) \\)</span> is one of the integers in the closed interval <span>\\( [-\mathop{d}(A,B), \mathop{d}(A,B)]. \\)</span> Now for any given integer <span>\\( k \\)</span>, the points <span>\\( Q \\)</span> satisfying <span>\\( \mathop{d}(A,Q) - \mathop{d}(B,Q) = k \\)</span> all lie on a branch of a hyperbola (or the degenerate cases: a straight line parallel or perpendicular to the line through <span>\\( A \\)</span> and <span>\\( B \\)</span>). Every point of the set <span>\\( S \\)</span> is an intersection of one of these curves, and one of the analogous curves for <span>\\( A \\)</span> and <span>\\( C \\)</span>, and one of the curves for <span>\\( B \\)</span> and <span>\\( C \\)</span>. But any two of the curves intersect in only a finite number of points. Therefore there are only a finite number of points with integer distances from <span>\\( A \\)</span>, <span>\\( B \\)</span> and <span>\\( C. \\)</span>  This is a contradiction!


Ralph conjectures too that the same result holds if the points lie in any other higher-dimension space:

<div class="well">
I conjecture that the same is true in three and higher dimensions. That is: if \( S \) is an infinite set of points in \( \mathbb{R}^d \) such that the distance between any two is an integer, then the points of \( S \) are colinear.
</div>

How would you prove this conjecture?
