---
layout: page
title: A plateau function
date: 2010-09-24 19:07:33.000000000 -04:00
category: course-material
topic: distributions
comments: true
---

The goal of this page is to show the existence, for any compact set <span>\\( K \subset \mathbb{R}^d \\)</span>, of functions <span>\\( \psi\colon \mathbb{R}^d \to \mathbb{R} \\)</span> which are non-negative, infinitely differentiable, with compact support, and with a constant positive value in a neighborhood of the set <span>\\( K \\)</span>.  A construction of such function is presented here:

Let <span>\\( f\colon \mathbb{R} \to \mathbb{R} \\)</span> defined piecewise by:

<table style="border-width:0;margin-left:auto; margin-right:auto;">
<tbody>
<tr>
<td style="vertical-align:middle;border-width:0;">\( f(t) = \begin{cases} \exp (-1/t) & \text{if } t>0 \\ 0&  \text{otherwise}\end{cases} \)</span></td>
<td style="border-width:0;"><a href="http://blancosilva.files.wordpress.com/2010/09/msp106919cacf0cih9fhe3f00002cc7h1746c29gf70.gif"><img class="aligncenter size-full wp-image-409" title="MSP106919cacf0cih9fhe3f00002cc7h1746c29gf70" src="https://blancosilva.files.wordpress.com/2010/09/msp106919cacf0cih9fhe3f00002cc7h1746c29gf70.gif?w=595" alt="" width="300" height="199" /></a></td>
</tr>
</tbody>
</table>

We need to prove that this function is <span>\\( C^\infty \\)</span>.  The following result helps:

<div class="well">
<h4>Theorem</h4>

If \( P \) is a polynomial and \( g(t) = P(1/t) \exp(-1/t) \) for \( t>0 \), \( g(t) = 0 \) for \( t\leq 0 \), then \( g \) is continuous.  The derivative for \( t \neq 0 \) is of the same form with \( P(1/t) \) replaced by \( \big( P(1/t) - P'(1/t)\big) / t^2 \), so \( g'(0) \) exists and is equal to zero.
</div>

Consider now for any dimension <span>\\( d \in \mathbb{N} \\)</span> the function <span>\\( \phi\colon \mathbb{R}^d \to \mathbb{R} \\)</span> defined below.  It is non-negative, infinitely differentiable, with compact support, and it satisfies <span>\\( \phi(0) > 0 \\)</span>. Notice that the support of <span>\\( \phi \\)</span> is the ball of radius 1 centered at the origin.

<div>
	\begin{equation}
	\phi(\boldsymbol{x}) = f(1-\lvert \boldsymbol{x} \rvert^2) \text{ with } \lvert \boldsymbol{x} \rvert^2 = \sum_{k=1}^d x_k^2 \text{ for any } \boldsymbol{x} = (x_1, \dotsc, x_d) \in \mathbb{R}^d
	\end{equation}
</div>

<p style="text-align:center;border-width:0;">
	<img src="https://blancosilva.files.wordpress.com/2010/09/msp115219cacg2fefhc1ec000005dgd99c5gc5icefd.gif?w=595" alt="" style="width:300;height:199" />
</p>

We can obtain a similar *bump* function with support in a ball centered at any location <span>\\( \boldsymbol{x}_0 \in \mathbb{R}^d \\)</span> and with radius <span>\\( \delta>0 \\)</span>, by the usual translation and change of scales of the previous function <span>\\( \phi: \\)</span>

<div>
	\begin{equation}
	\boldsymbol{x} \mapsto \phi \bigg( \frac{\boldsymbol{x} - \boldsymbol{x}_0}{\delta} \bigg)
	\end{equation}
</div>

In the last step we accomplish the last desired property.  For this task, we will construct the function by convolution of a bump function with the indicator of a small ball containing the given compact set.  This convolution preserves both the *best* integrability and smoothness properties of the functions used to construct it, and so we obtain the desired result:

Let <span>\\( K \subset \mathbb{R}^d \\)</span> be a compact set, and let <span>\\( \boldsymbol{x}_0 \in K \\)</span> and <span>\\( \delta>0 \\)</span> such that <span>\\( K \subset B_\delta (\boldsymbol{x}_0) \\)</span>. Consider the functions <span>\\( u = \boldsymbol{\chi}\_{B\_{2\delta}(\boldsymbol{x}\_0)} \\)</span>—the indicator function of the ball with radius <span>\\( 2\delta \\)</span> centered in <span>\\( \boldsymbol{x}_0 \\)</span>—and the bump funtcion <span>\\( v(\boldsymbol{x}) = \phi(\boldsymbol{x}/\delta) \\)</span>, with support in the ball of radius <span>\\( \delta \\)</span> centered at the origin.  It is then

<div>
	\begin{align}
	\big( u \ast v \big) (x) & = \int_{\mathbb{R}^d} u(x-y) v(y)\, dy \\
    & = \int_{B_\delta(\boldsymbol{0})} \boldsymbol{\chi}_{B_{2\delta}(\boldsymbol{x}_0)}(x-y) \phi(y/\delta)\, dy
    \end{equation}
</div>

Notice that, by construction, this function satisfies:

1. <span>\\( u \ast v \\)</span> is non-negative.</li>
2. <span>\\( u \ast v \in C_c^\infty (\mathbb{R}^d) \\)</span>.</li>
3. <span>\\( 0 \leq \big( u \ast v \big) (\boldsymbol{x}) \leq \lVert \phi \rVert_1 \\)</span> for all <span>\\( \boldsymbol{x} \in \mathbb{R}^d \\)</span>.</li>
4. <span>\\( \big( u \ast v \big) (\boldsymbol{x}) = 0 \\)</span> if <span>\\( \lvert \boldsymbol{x}-\boldsymbol{x}_0 \rvert \geq 2\delta \\)</span>.</li>
5. <span>\\( \big( u \ast v \big) (\boldsymbol{x}) = \lVert \phi \rVert_1 \\)</span> if <span>\\( \lvert \boldsymbol{x}-\boldsymbol{x}_0 \rvert &lt; \delta \\)</span> (in particular, for all <span>\\( \boldsymbol{x} \in K \\)</span>)</li>
