---
layout: page
title: Convolution of integrable functions
date: 2010-09-26 20:47:07.000000000 -04:00
category: course-material
topic: distributions
comments: true
---

Suppose that <span>\\( f, g \\)</span> are Lebesgue-integrable functions in a d–dimensional Euclidean space <span>\\( \mathbb{R}^d \\)</span>. The convolution of <span>\\( f \\)</span> and <span>\\( g \\)</span> is defined by

<div>
	\begin{equation}
	\big( f \ast g \big) (x) = \int_{\mathbb{R}^d} f(y) g(x-y)\, dy.
	\end{equation}
</div>

The operation is closed in the space of integrable functions:

<div class="well">
If \( f, g \in L_1(\mathbb{R}^d) \), then \( \displaystyle{ \int_{\mathbb{R}^d} \lvert f(y)\rvert\, \lvert g(x-y) \rvert\, dy &lt; \infty} \) for a.e. \( x \in \mathbb{R}^d \).
</div>

Indeed; notice that the function <span>\\( h\colon \mathbb{R}^d \times \mathbb{R}^d \to \mathbb{R} \\)</span> defined by <span>\\( h(x,y) = \lvert f(y) g(x-y) \rvert \\)</span> is measurable and non-negative.  By Tonelli's Theorem, the iterated integrals are equal and thus

<div>
	\begin{align} 
	\int_{\mathbb{R}^d} \int_{\mathbb{R}^d} \lvert f(y)\rvert\, \lvert g(x-y)\rvert \, dy\, dx & =
	\int_{\mathbb{R}^d} \int_{\mathbb{R}^d} \lvert f(y) \rvert\, \lvert g(x-y) \rvert\, dx\, dy \\
	& = \int_{\mathbb{R}^d} \bigg( \int_{\mathbb{R}^d} \lvert g(x-y) \rvert\, dx \bigg) \lvert f(y) \rvert\, dy \\
	& = \lVert g \rVert_1 \lVert f \rVert_1
	\end{align}
</div>

Notice that the operation is commutative (by virtue of the translation-invariance of the Lebesque measure):   For all <span>\\( x \in \mathbb{R}^d \\)</span> where the convolution is well-defined,

<div>
	\begin{equation}
	\big( g \ast f \big) (x) = \int_{\mathbb{R}^d} f(x-y)\, g(y)\, dy = \int_{\mathbb{R}^d} f(y)\, g(x-y)\, dy = \big( f \ast g \big) (x).
	\end{equation}
</div>

Unfortunately, there is no unit for this operation, and thus <span>\\( \big( L_1(\mathbb{R}^d), + , \ast \big) \\)</span> does not have the structure of an algebraic ring.

The convolution is also well-defined in a general <span>\\( L_p \\)</span> space for <span>\\( 1 \leq p \leq \infty \\)</span>, with the following fundamental result:

<div class="well">
	Suppose \( g \in L_1(\mathbb{R}^d) \), \( f \in L_p(\mathbb{R}^d) \) for \( 1 \leq p \leq \infty \).  Then \( f \ast g \) is a well-defined \( L_p(\mathbb{R}^d) \) function satisfying \( \lVert f \ast g \rVert_p \leq \lVert g \rVert_1\, \lVert f \rVert_p \).
</div>

This is direct using Tonelli's Theorem and Hölder's Inequality: Assume <span>\\( f \\)</span> and <span>\\( g \\)</span> are non-negative, and let <span>\\( q&gt;0 \\)</span> such that <span>\\( \frac{1}{p} + \frac{1}{q} =1 \\)</span>.

<div>
	\begin{align}
	\lVert f \ast g \rVert_p^p &=
	\int_{\mathbb{R}^d} \bigg( \int_{\mathbb{R}^d} g(y)^{1/p} g(y)^{1-1/p} f(x-y)\,  dy \bigg)^p dx \\
	& \leq \int_{\mathbb{R}^d} \bigg( \int_{\mathbb{R}^d} g(y)^{p \cdot 1/p} f(x-y)^p dy \bigg) \bigg( \int_{\mathbb{R}^d} g(y)^{q \cdot 1/q} dy \bigg)^{p/q}\, dx \\
	& = \lVert g \rVert_1 \lVert f \rVert_p^p \lVert g \rVert_1^{p/q} = \lVert g \rVert_1^p \lVert f \rVert_p^p.
	\end{align}
</div>

Another interesting property of the convolution is that it preserves the *best* smoothness, provided the smooth function has compact support:

<div class="well">
	Suppose \( f \in L_p(\mathbb{R}^d) \) for \( 1 \leq p \leq \infty \), and \( \phi \in C_c^m(\mathbb{R}^d) \) for some \( m \geq 1 \).  Then \( f \ast \phi \in L_p(\mathbb{R}^d) \cap C^m(\mathbb{R}^d) \).
</div>

The continuity follows easily, as it does the fact that the convolution is in <span>\\( L_p(\mathbb{R}^d) \\)</span>.  To prove the statement concerning the smoothness, it will be enough to show that for the partial differential operator <span>\\( D=\frac{\partial}{\partial x_1} \\)</span>, it is <span>\\( D( f \ast \phi) = f \ast D\phi \\)</span>.
