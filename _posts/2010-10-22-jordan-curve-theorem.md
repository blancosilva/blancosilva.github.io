---
layout: post
title: The Jordan Curve Theorem
date: 2010-10-22 13:37:01.000000000 -04:00
category: post
comments: true
---

The first time I faced this challenge was in the stage of my second Analysis course in College.  The instructor needed this result for one of the proofs in class, stated it, and claimed that "you would need some more miles under your belts to be able to find—and understand—a proof of it."  It goes like this:

<div class="well">
Let \( \phi \colon \mathbb{S}^1 \to \mathbb{R}^2 \) be an injective, continuous map from the circle \( \mathbb{S}^1 \) to the Euclidean plane \( \mathbb{R}^2 \).  We say that the image of this map is a <strong>Jordan curve</strong>—a non-self-intersecting continuous loop in the plane.

The complement \( \mathbb{R}^2 \setminus C \) of a Jordan curve \( C=\text{img} (\phi) \) in the plane consists on two connected components: one of them is bounded, and the other unbounded. The curve \( C \) is the boundary of both components.
</blockquote>

How is it possible that such a basic and intuitive statement does need "a proof"?  Isn't it evident?  This is one of those cases in which Mathematics can turn frustrating for a moment: somehow one feels like Pandora after opening the infamous box.  The source of that frustration relies on the impossibility of coming up with a devastating reasoning on the spot to prove that the statement is indeed true.  Where does one start?

Two years later, in the scope of Algebraic Topology while toying with Homology Theory, the instructor pointed to "an amusing application of the Mayer-Vietoris sequence":

If <span>\\( X \subset \mathbb{R}^d \\)</span> is a subset of the Euclidean <span>\\( d \\)</span>–dimensional space <span>\\( \mathbb{R}^d \\)</span> which is homeomorphic to a <span>\\( k \\)</span>–sphere (for any <span>\\( 0 \leq k \leq d-1 \\)</span>), then the reduced integral homology groups <span>\\( \widetilde{H}_q(Y) \\)</span> of <span>\\( Y = \mathbb{R}^d \setminus X \\)</span> are given by

<div>
	\begin{equation}
	\widetilde{H}_q(Y) = \begin{cases} \mathbb{Z} & \text{if }q=d-1-k \\ 0 &  \text{otherwise} \end{cases}
	\end{equation}
</div>

This "simple" application of the Mayer-Vietoris sequence, when considering the case <span>\\( d=2 \\)</span>, <span>\\( k=1 \\)</span> and <span>\\( X=C=\text{img}(\phi) \\)</span>, gives us a proof of the Jordan Curve Theorem as corollary!

Let us trace back a few steps, and try to go over enough Homology Theory to understand what those results are about, and why the computation of the reduced integral homology group <span>\\( \widetilde{H}_0(\mathbb{R}^2 \setminus C) \\)</span> casts any light on connected components and boundedness.
