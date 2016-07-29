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
			<td style="text-align:justify;font-family:modern;font-size:12pt;width:50%;border-width:0;">
				If <span>\\( h_n \\)</span> has no fixed point, then it is possible to draw, for each <span>\\( x \in \overline{B_d} \\)</span>, a ray through \\( x \\) emanating from <span>\\( h_n(x) \\)</span>.  This ray intersects <span>\\( \mathbb{S}_{d-1} \\)</span> at a single point, which we denote <span>\\( f_n(x) \\)</span>.   The function <span>\\( f_n \colon \overline{B_d} \to \mathbb{S}_{d-1} \\)</span> thus defined is \\( C^1 \\) and satisfies <span>\\( f_n(x) = x \\)</span> for all <span>\\( x \in \mathbb{S}_{d-1} \\)</span>, contradicting the previous result.
			</td>
		</tr>
	</tbody>
</table>

This implies, as we announced before, the existence of a sequence of points <img src="https://s0.wp.com/latex.php?latex=x_n+%5Cin+%5Coverline%7BB_d%7D&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="x_n &#92;in &#92;overline{B_d}" title="x_n &#92;in &#92;overline{B_d}" class="latex" /> satisfying <img src="https://s0.wp.com/latex.php?latex=h_n%28x_n%29+%3D+x_n.&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="h_n(x_n) = x_n." title="h_n(x_n) = x_n." class="latex" /> The compactness of <img src="https://s0.wp.com/latex.php?latex=%5Coverline%7BB_d%7D&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="&#92;overline{B_d}" title="&#92;overline{B_d}" class="latex" /> guarantees a convergent subsequence <img src="https://s0.wp.com/latex.php?latex=%5Cbig%28+x_%7Bn_r%7D+%5Cbig%29_%7Br+%5Cin+%5Cmathbb%7BN%7D%7D&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="&#92;big( x_{n_r} &#92;big)_{r &#92;in &#92;mathbb{N}}" title="&#92;big( x_{n_r} &#92;big)_{r &#92;in &#92;mathbb{N}}" class="latex" />.  Let <img src="https://s0.wp.com/latex.php?latex=x_0+%5Cin+%5Coverline%7BB_d%7D&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="x_0 &#92;in &#92;overline{B_d}" title="x_0 &#92;in &#92;overline{B_d}" class="latex" /> be its limit.  It must be then

<p style="text-align:center;"><img src="https://s0.wp.com/latex.php?latex=%5Cdisplaystyle%7Bf%28x_0%29+%3D+%5Clim_r+f%28x_%7Bn_r%7D%29+%3D+%5Clim_r+h_%7Bn_r%7D%28x_%7Bn_r%7D%29+%3D+%5Clim_r+x_%7Bn_r%7D+%3D+x_0%7D%2C&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="&#92;displaystyle{f(x_0) = &#92;lim_r f(x_{n_r}) = &#92;lim_r h_{n_r}(x_{n_r}) = &#92;lim_r x_{n_r} = x_0}," title="&#92;displaystyle{f(x_0) = &#92;lim_r f(x_{n_r}) = &#92;lim_r h_{n_r}(x_{n_r}) = &#92;lim_r x_{n_r} = x_0}," class="latex" /></p>

and we have just found a fixed point for <img src="https://s0.wp.com/latex.php?latex=f.&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="f." title="f." class="latex" />

The proof of the Theorem for continuous functions <img src="https://s0.wp.com/latex.php?latex=f%5Ccolon+K+%5Cto+K&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="f&#92;colon K &#92;to K" title="f&#92;colon K &#92;to K" class="latex" /> for a given convex compact set <img src="https://s0.wp.com/latex.php?latex=K%5Csubset%5Cmathbb%7BR%7D%5Ed&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="K&#92;subset&#92;mathbb{R}^d" title="K&#92;subset&#92;mathbb{R}^d" class="latex" /> is done through an appropriate homeomorphism <img src="https://s0.wp.com/latex.php?latex=%5Cvarphi%5Ccolon+B_d+%5Cto+K.&#038;bg=ffffff&#038;fg=555555&#038;s=0" alt="&#92;varphi&#92;colon B_d &#92;to K." title="&#92;varphi&#92;colon B_d &#92;to K." class="latex" />

<h3 style="text-align:justify;font-family:modern;">Miscellaneous</h3>

Note that the Brouwer Fixed Point Theorem is not constructive: although the proof indicates how to come up with a fixed point, there is no explicit construction that finds such point.  The key here is the Stone-Weierstrass Theorem, that claims the existence of a sequence of polynomials, but does not compute them.

We can find nonetheless a constructive version of a Fixed Point Theorem in the field of Analysis: the Banach Fixed Point Theorem.  This result gives a general criterion that guaranties that, if satisfied, the procedure of iterating a function will yield a fixed point.

> Let <img src="https://s0.wp.com/latex.php?latex=%28X%2C+%5ClVert+%5Ccdot+%5CrVert%29&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="(X, &#92;lVert &#92;cdot &#92;rVert)" title="(X, &#92;lVert &#92;cdot &#92;rVert)" class="latex" /> be a non-empty complete metric space. Let <img src="https://s0.wp.com/latex.php?latex=T+%5Ccolon+X+%5Cto+X&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="T &#92;colon X &#92;to X" title="T &#92;colon X &#92;to X" class="latex" /> be a contraction mapping on <img src="https://s0.wp.com/latex.php?latex=X&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="X" title="X" class="latex" />, i.e.: there is a nonnegative real number <img src="https://s0.wp.com/latex.php?latex=q+%3C+1&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="q &lt; 1" title="q &lt; 1" class="latex" /> such that
<p style="text-align:center;font-family:modern;font-size:12pt;"><img src="https://s0.wp.com/latex.php?latex=%5ClVert+T%28x%29+-+T%28y%29+%5CrVert+%5Cleq+q%5ClVert+x-y%5CrVert&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="&#92;lVert T(x) - T(y) &#92;rVert &#92;leq q&#92;lVert x-y&#92;rVert" title="&#92;lVert T(x) - T(y) &#92;rVert &#92;leq q&#92;lVert x-y&#92;rVert" class="latex" /> for all <img src="https://s0.wp.com/latex.php?latex=x%2Cy+%5Cin+X.&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="x,y &#92;in X." title="x,y &#92;in X." class="latex" />

for all <img src="https://s0.wp.com/latex.php?latex=x%2C+y+%5Cin+X.&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="x, y &#92;in X." title="x, y &#92;in X." class="latex" /> Then the map <img src="https://s0.wp.com/latex.php?latex=T&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="T" title="T" class="latex" /> admits one and only one fixed point in <img src="https://s0.wp.com/latex.php?latex=X.&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="X." title="X." class="latex" /> Furthermore, this fixed point can be found as follows: start with an arbitrary element <img src="https://s0.wp.com/latex.php?latex=x_0&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="x_0" title="x_0" class="latex" /> in <img src="https://s0.wp.com/latex.php?latex=X&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="X" title="X" class="latex" /> and define an iterative sequence by <img src="https://s0.wp.com/latex.php?latex=x_n%3DT%28x_%7Bn-1%7D%29&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="x_n=T(x_{n-1})" title="x_n=T(x_{n-1})" class="latex" /> for <img src="https://s0.wp.com/latex.php?latex=n+%5Cin+%5Cmathbb%7BN%7D.&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="n &#92;in &#92;mathbb{N}." title="n &#92;in &#92;mathbb{N}." class="latex" /> This sequence converges, and its limit is the fixed point of <img src="https://s0.wp.com/latex.php?latex=T.&#038;bg=F4F5F7&#038;fg=555555&#038;s=0" alt="T." title="T." class="latex" />

Other versions also allow us to count how many fixed points will be for a given function.  That is the case of both the Lefschetz and the Nielsen Fixed Point Theorems.

<h3 style="font-family:modern;font-size:12pt;">References</h3>

<p style="text-align:center;"><a href="http://www.amazon.com/gp/product/0131816292/ref=as_li_tf_il?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399377&amp;creativeASIN=0131816292"><img border="0" src="http://ws.assoc-amazon.com/widgets/q?_encoding=UTF8&amp;Format=_SL160_&amp;ASIN=0131816292&amp;MarketPlace=US&amp;ID=AsinImage&amp;WS=1&amp;tag=blancosilva-20&amp;ServiceVersion=20070822"></a><img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=0131816292&amp;camp=217145&amp;creative=399377" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" /><br /><a href="http://www.amazon.com/gp/product/0131816292/ref=as_li_tf_tl?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399377&amp;creativeASIN=0131816292">Topology (2nd Edition)</a><img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=0131816292&amp;camp=217145&amp;creative=399377" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" /> (See all <a href="http://www.amazon.com/Topology-Geometry-Mathematics-Science-Books/b/ref=as_li_tf_tl?ie=UTF8&amp;tag=blancosilva-20&amp;linkCode=as2&amp;camp=217145&amp;creative=399385&amp;creativeASIN=0131816292&amp;ie=UTF8&amp;node=13987">Topology Books</a>)<img src="http://www.assoc-amazon.com/e/ir?t=blancosilva-20&amp;l=as2&amp;o=1&amp;a=0131816292&amp;camp=217145&amp;creative=399385" width="1" height="1" border="0" alt="" style="border:none!important;margin:0!important;" /></p>
