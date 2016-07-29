---
title: Borsuk-Ulam and Fixed Point Theorems
layout: post
category: post
comments: true
image:
teaser: "https://i1.wp.com/farm6.static.flickr.com/5208/5224985241_813dab62b3_o_d.jpg"
---

At any given moment on the surface of the Earth there are always two antipodal points with exactly the same temperature and barometric pressure.  We can go even further: on each longitude (the North and South lines running from pole to pole) there will also be two antipodal points sharing exactly the same temperature.  How is this possible?  The answer is given by the Borsuk-Ulam Theorem: a powerful tool in Topology with a great deal of applications to every branch of science.

> A continuous function \\( f \colon \mathbb{S}_d \to \mathbb{R}^d \\) from a *d*--dimensional sphere into the Euclidean space of dimension *c* maps some pair of antipodal points \\( \pm \xi \in \mathbb{S}_d\\) to the same point \\( \boldsymbol{x} \in \mathbb{R}^d \\)

The implications of this Theorem are huge.  Some of the most useful are cited below:

+ No subset of \\( \mathbb{R}^d \\) can be homeomorphic to a *d*--dimensional sphere \\( \mathbb{S}_d \\)
+ If we cover the sphere \\( \mathbb{S}_d \\) with a family of \\( d+1 \\) open sets,  then at least one of these sets must contain a pair of antipodal points \\( \pm \xi \\).

But the most useful application of Borsuk-Ulam is without a doubt the Brouwer Fixed Point Theorem.

> Every continuous function \\( f \colon K \to K \\) from a convex compact subset \\( K \subset \mathbb{R}^d \\) of a Euclidean space to itself has a fixed point.

The proof of Brouwer Fixed Point from Borsuk-Ulam is immediate, and I urge the readers to find it by themselves as a nice exercise.  There are many different proofs of Brouwer Fixed Point without Borsuk-Ulam, the simplest of them all, done by C.A. Rogers as a simplification of a previous proof by J.W. Milnor: it uses the most basic of mathematics, accesible to students with knowledge of elementary integral Calculus.

A version of this proof starts by showing that there are no differentiable maps with continuous derivative, from a closed ball to its border, that fixes all points in that sphere:

> Let \\( B_d \subset \mathbb{R}^d \\) denote the unit ball in the Euclidean *d*--space, whose border is the \\( (d-1)\\)--dimensional sphere 
<span>\\( \mathbb{S}_{d-1}. \\)</span>   There is no \\( C^1 \\) map (once-differentiable with continuous derivative)  <span>\\( f \colon \overline{B_d} \to \mathbb{S}_{d-1} \\)</span> such that \\( f(\boldsymbol{x}) = \boldsymbol{x} \\) for all <span>\\( \boldsymbol{x} \in \mathbb{S}_{d-1}. \\)</span>

The use of the previous result together with the Stone-Weierstrass Theorem guarantees the existence of fixed points for any continuous function <span>\\( f \colon \overline{B_d} \to \overline{B_d}. \\)</span>

Indeed, the Stone-Weierstrass Theorem gives the existence, for each \\( n \in \mathbb{N} \\) of a polynomial <span>\\( P_n \colon \overline{B_d} \to \mathbb{R}^d \\)</span> satisfying <span>\\( \lVert f - P_n \rVert_2 \leq \frac{1}{n} \\)</span>.  Consider the sequence of functions <span>\\( h_n = \frac{n}{n+1} P_n \colon \overline{B_d} \to \overline{B_d} \\)</span>, which converges uniformly to \\( f \\).

We claim that each function <span>\\( h_n \\)</span> has a fixed point <span>\\( x_n \in \overline{B_d} \\)</span>.  If this were not true, we would be able to construct \\( C^1 \\) functions <span>\\( f_n \colon \overline{B_d} \to \mathbb{S}_{d-1} \\)</span> satisfying <span>\\( f_n(\boldsymbol{x}) = \boldsymbol{x} \\)</span> for all <span>\\( \boldsymbol{x} \in \mathbb{S}_{d-1} \\)</span>  Such a construction could be as follows:

<table style="width:99%;margin-left:auto;margin-right:auto;border-style:dotted;border-width:1pt;">
	<tbody>
		<tr>
			<td style="vertical-align:middle;width:40%;border-width:0;">
				<img src="https://i1.wp.com/farm6.static.flickr.com/5208/5224985241_813dab62b3_o_d.jpg" alt="" width="100%" />
			</td>
			<td style="width:10%"></td>
			<td style="text-align:justify;font-family:modern;font-size:12pt;width:40%;border-width:0;">
				If <span>\( h_n \)</span> has no fixed point, then it is possible to draw, for each <span>\( x \in \overline{B_d} \)</span>, a ray through \( x \) emanating from <span>\( h_n(x) \)</span>.  This ray intersects <span>\( \mathbb{S}_{d-1} \)</span> at a single point, which we denote <span>\( f_n(x) \)</span>.   The function <span>\( f_n \colon \overline{B_d} \to \mathbb{S}_{d-1} \)</span> thus defined is \( C^1 \) and satisfies <span>\( f_n(x) = x \)</span> for all <span>\( x \in \mathbb{S}_{d-1} \)</span>, contradicting the previous result.
			</td>
			<td style="width:10%"></td>
		</tr>
	</tbody>
</table>

This implies, as we announced before, the existence of a sequence of points <span>\\( x_n \in \overline{B_d} \\)</span> satisfying <span>\\( h_n(x_n) = x_n \\)</span>.  The compactness of <span>\\( \overline{B_d} \\)</span> guarantees a convergent subsequence <span>\\( \big( x_{n_r} \big)_{r \in \mathbb{N}} \\)</span>.  Let <span>\\( x_0 \in \overline{B_d} \\)</span> be its limit.  It must be then

<p style="text-align:center;">
	<span>
		\( f(x_0) = \lim_r f(x_{n_r}) = \lim_r h_{n_r} (x_{n_r}) = \lim_r x_{n_r} = x_0 \)
	</span>
</p>

and we have just found a fixed point for \\( f \\).

The proof of the Theorem for continuous functions \\( f \colon K \to K \\) for a given convex compact set \\( K \subset \mathbb{R}^d \\) is done through an appropriate homeomorphism <span>\\( \phi \colon \overline{B_d} \to K \\)</span>.

<h3 style="text-align:justify;font-family:modern;">Miscellaneous</h3>

Note that the Brouwer Fixed Point Theorem is not constructive: although the proof indicates how to come up with a fixed point, there is no explicit construction that finds such point.  The key here is the Stone-Weierstrass Theorem, that claims the existence of a sequence of polynomials, but does not compute them.

We can find nonetheless a constructive version of a Fixed Point Theorem in the field of Analysis: the Banach Fixed Point Theorem.  This result gives a general criterion that guaranties that, if satisfied, the procedure of iterating a function will yield a fixed point.

> Let \\( \big( X, \lVert \cdot \rVert \big) \\) be a non-empty complete metric space. Let \\( T \colon X \to X \\) be a contraction mapping on \\( X \\), i.e.: there is a nonnegative real number \\( q < 1 \\) such that \\( \lVert T(x) - T(y) \rVert \leq q \lVert x - y \rVert \\) for all \\( x, y \in X \\). Then the map \\( T \\) admits one and only one fixed point in \\( X \\). Furthermore, this fixed point can be found as follows: start with an arbitrary element <span>\\( x_0 \in X \\)</span> and define an iterative sequence by <span>\\( x_n = T(x_{n-1}) \\)<span> for \\( n \in \mathbb{N} \\). This sequence converges, and its limit is the fixed point of \\( T \\).

Other versions also allow us to count how many fixed points will be for a given function.  That is the case of both the Lefschetz and the Nielsen Fixed Point Theorems.

<h3 style="font-family:modern;font-size:12pt;">References</h3>

<p style="text-align:center;"><a href="http://www.amazon.com/gp/product/0131816292/ref=as_li_tf_il?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399377&amp;creativeASIN=0131816292"><img border="0" src="http://ws.assoc-amazon.com/widgets/q?_encoding=UTF8&amp;Format=_SL160_&amp;ASIN=0131816292&amp;MarketPlace=US&amp;ID=AsinImage&amp;WS=1&amp;tag=blancosilva-20&amp;ServiceVersion=20070822"></a><img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=0131816292&amp;camp=217145&amp;creative=399377" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" /><br /><a href="http://www.amazon.com/gp/product/0131816292/ref=as_li_tf_tl?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399377&amp;creativeASIN=0131816292">Topology (2nd Edition)</a><img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=0131816292&amp;camp=217145&amp;creative=399377" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" /><br/> (See all <a href="http://www.amazon.com/Topology-Geometry-Mathematics-Science-Books/b/ref=as_li_tf_tl?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399385&amp;creativeASIN=0131816292&amp;ie=UTF8&amp;node=13987">Topology Books</a>)<img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=0131816292&amp;camp=217145&amp;creative=399385" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" /></p>
