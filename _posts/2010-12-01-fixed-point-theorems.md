---
layout: post
title: Borsuk-Ulam and Fixed Point Theorems
comments: true
category: post
image:
  teaser: http://farm6.static.flickr.com/5208/5224985241_813dab62b3_o_d.jpg
---

At any given moment on the surface of the Earth there are always two antipodal points with exactly the same temperature and barometric pressure.  We can go even further: on each longitude (the North and South lines running from pole to pole) there will also be two antipodal points sharing exactly the same temperature.  How is this possible?  The answer is given by the Borsuk-Ulam Theorem: a powerful tool in Topology with a great deal of applications to every branch of science.

> A continuous function \\( f\colon \mathbb{S}\_{d} \to \mathbb{R}^d\\) from a \\( d \\)-dimensional sphere into the Euclidean space of dimension \\( d \\) maps some pair of antipodal points \\( \pm \xi \in \mathbb{S}\_{d} \\) to the same point \\( \boldsymbol{x} \in \mathbb{R}^d. \\)

The implications of this Theorem are huge.  Some of the most useful are cited below:

* No subset of <span>\\( \mathbb{R}^d \\)</span> can be homeomorphic to a <span>\\( d \\)</span>-dimensional sphere <span>\\( \mathbb{S}_{d}. \\)</span>
*  If we cover the sphere <span>\\( \mathbb{S}_d \\)</span> with a family of <span>\\( d+1 \\)</span> open sets,  then at least one of these sets must contain a pair of antipodal points <span>\\( \pm\xi. \\)</span>

But the most useful application of Borsuk-Ulam is without a doubt the Brouwer Fixed Point Theorem.

> Every continuous function \\( f\colon K \to K \\) from a convex compact subset \\( K\subset \mathbb{R}^d \\) of a Euclidean space to itself has a fixed point.

The proof of Brouwer Fixed Point from Borsuk-Ulam is immediate, and I urge the readers to find it by themselves as a nice exercise.  There are many different proofs of Brouwer Fixed Point without Borsuk-Ulam, the simplest of them all, done by C.A.Rogers as a simplification of a previous proof by J.W.Milnor: it uses the most basic of mathematics, accessible to students with knowledge of elementary integral Calculus.

A version of this proof starts by showing that there are no differentiable maps with continuous derivative, from a closed ball to its border, that fixes all points in that sphere:

> Let \\( B_d\subset \mathbb{R}^d \\) denote the unit ball in the Euclidean \\( d \\)-space, whose border is the \\( (d-1) \\)-dimensional sphere \\( \mathbb{S}\_{d-1}. \\)   There is no \\( C^1 \\) map (once-differentiable with continuous derivative) \\( f\colon \overline{B\_d} \to \mathbb{S}^{d-1} \\) such that \\( f(x) = x \\) for all \\( x \in \mathbb{S}\_{d-1}. \\)

The use of the previous result together with the Stone-Weierstrass Theorem guarantees the existence of fixed points for any continuous function <span>\\( f\colon \overline{B_d} \to \overline{B_d}. \\)</span>

Indeed, the Stone-Weierstrass Theorem gives the existence, for each <span>\\( n\in \mathbb{N}, \\)</span> of a polynomial <span>\\( P_n\colon \overline{B_d} \to \mathbb{R}^d \\)</span> satisfying <span>\\( \lVert f-P_n \rVert_2 \leq \tfrac{1}{n}. \\)</span>  Consider the sequence of functions <span>\\( h_n(x) = \tfrac{n}{n+1}P_n\colon \overline{B_d} \to \overline{B_d}, \\)</span> which converges uniformly to <span>\\( f. \\)</span>

We claim that each function <span>\\( h_n \\)</span> has a fixed point <span>\\( x_n \in \overline{B_d}, \\)</span> <span>\\( h_n(x_n) = x_n. \\)</span>  If this were not true, we would be able to construct <span>\\( C^1 \\)</span> functions <span>\\( f_n\colon \overline{B_d} \to \mathbb{S}_{d-1} \\)</span> satisfying <span>\\( f_n(x) = x \\)</span> for all <span>\\( x \in \mathbb{S}_{d-1}. \\)</span>  Such a construction could be as follows:

<table style="width:99%;margin-left:auto;margin-right:auto;border-style:dotted;border-width:1pt;">
<tbody>
<tr>
<td style="vertical-align:middle;width:40%;border-width:0;"><img src="http://farm6.static.flickr.com/5208/5224985241_813dab62b3_o_d.jpg" alt="" width="100%" /></td>
<td style="width:60%;padding:10px;">If \( h_n \) has no fixed point, then it is possible to draw, for each \( x \in \overline{B_d} \), a ray through \( x \) emanating from \( h_n(x) \).  This ray intersects \( \mathbb{S}_{d-1} \) at a single point, which we denote \( f_n(x). \)  The function \( f_n\colon \overline{B_d} \to \mathbb{S}_{d-1} \) thus defined is \( C^1 \) and satisfies \( f_n(x) = x \) for all \( x \in \mathbb{S}_{d-1}, \) contradicting the previous result.</td>
</tr>
</tbody>
</table>

<br />

This implies, as we announced before, the existence of a sequence of points <span>\\( x_n \in \overline{B_d} \\)</span> satisfying <span>\\( h_n(x_n) = x_n. \\)</span> The compactness of <span>\\( \overline{B_d} \\)</span> guarantees a convergent subsequence <span>\\( \big( x_{n_r} \big)_{r \in \mathbb{N}} \\)</span>.  Let <span>\\( x_0 \in \overline{B_d} \\)</span> be its limit.  It must be then

<div>
	\begin{equation}
	\displaystyle{f(x_0) = \lim_r f(x_{n_r}) = \lim_r h_{n_r}(x_{n_r}) = \lim_r x_{n_r} = x_0}, 
	\end{equation}
</div>

and we have just found a fixed point for <span>\\( f. \\)</span>

The proof of the Theorem for continuous functions <span>\\( f\colon K \to K \\)</span> for a given convex compact set <span>\\( K\subset\mathbb{R}^d \\)</span> is done through an appropriate homeomorphism <span>\\( \varphi\colon B_d \to K. \\)</span>

### Miscellaneous

Note that the Brouwer Fixed Point Theorem is not constructive: although the proof indicates how to come up with a fixed point, there is no explicit construction that finds such point.  The key here is the Stone-Weierstrass Theorem, that claims the existence of a sequence of polynomials, but does not compute them.

We can find nonetheless a constructive version of a Fixed Point Theorem in the field of Analysis: the Banach Fixed Point Theorem.  This result gives a general criterion that guaranties that, if satisfied, the procedure of iterating a function will yield a fixed point.

> Let \\( (X, \lVert \cdot \rVert) \\) be a non-empty complete metric space. Let \\( T \colon X \to X \\) be a contraction mapping on \\( X \\), i.e.: there is a nonnegative real number \\( q < 1 \\) such that
>
> \begin{equation} \lVert T(x) - T(y) \rVert \leq q\lVert x-y\rVert  \text{ for all } x,y \in X. \end{equation}
>
> for all \\( x, y \in X. \\) Then the map \\( T \\) admits one and only one fixed point in \\( X. \\) Furthermore, this fixed point can be found as follows: start with an arbitrary element \\( x_0 \\) in \\( X \\) and define an iterative sequence by \\( x\_n=T(x\_{n-1}) \\) for \\( n \in \mathbb{N}. \\) This sequence converges, and its limit is the fixed point of \\( T. \\)

Other versions also allow us to count how many fixed points will be for a given function.  That is the case of both the Lefschetz and the Nielsen Fixed Point Theorems.
