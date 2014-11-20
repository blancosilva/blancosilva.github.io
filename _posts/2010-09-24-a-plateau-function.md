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

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="text-align:center;vertical-align:middle;font-family:modern;font-size:12pt;border-width:0;">\( \phi(\boldsymbol{x}) = f(1-\lvert \boldsymbol{x} \rvert^2) \) with \( \lvert \boldsymbol{x} \rvert^2 = \displaystyle{\sum_{k=1}^d x_k^2} \) for any \( \boldsymbol{x} = (x_1, \dotsc, x_d) \in \mathbb{R}^d \)</td>
</tr>
<tr>
<td style="text-align:center;border-width:0;"><a href="http://blancosilva.files.wordpress.com/2010/09/msp115219cacg2fefhc1ec000005dgd99c5gc5icefd.gif"><img src="https://blancosilva.files.wordpress.com/2010/09/msp115219cacg2fefhc1ec000005dgd99c5gc5icefd.gif?w=595" alt="" width="300" height="199" /></a></td>
</tr>
</tbody>
</table>

We can obtain a similar <em>bump</em> function with support in a ball centered at any location <span>\\( \boldsymbol{x}_0 \in \mathbb{R}^d \\)</span> and with radius <span>\\( \delta>0 \\)</span>, by the usual translation and change of scales of the previous function <span>\\( \phi: \\)</span>

<table style="border:0;width:100%;">
<tbody>
<tr>
<td style="vertical-align:middle;text-align:center;border-width:0;"><span>\\( \boldsymbol{x} \mapsto \displaystyle{\phi \bigg( \frac{\boldsymbol{x} - \boldsymbol{x}_0}{\delta} \bigg)} \\)</span></td>
</tr>
</tbody>
</table>

In the last step we accomplish the last desired property.  For this task, we will construct the function by convolution of a bump function with the indicator of a small ball containing the given compact set.  This convolution preserves both the "<em>best</em>" integrability and smoothness properties of the functions used to construct it, and so we obtain the desired result:

Let <span>\\( K \subset \mathbb{R}^d \\)</span> be a compact set, and let <span>\\( \boldsymbol{x}_0 \in K \\)</span> and <span>\\( \delta>0 \\)</span> such that <span>\\( K \subset B_\delta (\boldsymbol{x}_0) \\)</span>. Consider the functions <span>\\( u = \boldsymbol{\chi}_{B_{2\delta}(\boldsymbol{x}_0)} \\)</span>—the indicator function of the ball with radius <span>\\( 2\delta \\)</span> centered in <span>\\( \boldsymbol{x}_0 \\)</span>—and the bump funtcion <span>\\( v(\boldsymbol{x}) = \phi(\boldsymbol{x}/\delta) \\)</span>, with support in the ball of radius <span>\\( \delta \\)</span> centered at the origin.  It is then

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="text-align:right;vertical-align:middle;border-width:0;"><span>\\( \big( u \ast v \big) (x) \\)</span></td>
<td style="text-align:left;border-width:0;"><span>\\( = \displaystyle{\int_{\mathbb{R}^d} u(x-y) v(y)\, dy} \\)</span></td>
</tr>
<tr>
<td style="border-width:0;"></td>
<td style="text-align:left;border-width:0;"><span>\\( = \displaystyle{\int_{B_\delta(\boldsymbol{0})} \boldsymbol{\chi}_{B_{2\delta}(\boldsymbol{x}_0)}(x-y) \phi(y/\delta)\, dy} \\)</span></td>
</tr>
</tbody>
</table>

Notice that, by construction, this function satisfies:
<ol>
<li style="text-align:justify;font-family:modern;font-size:12pt;"><span>\\( u \ast v \\)</span> is non-negative.</li>
<li style="text-align:justify;font-family:modern;font-size:12pt;"><span>\\( u \ast v \in C_c^\infty (\mathbb{R}^d) \\)</span>.</li>
<li style="text-align:justify;font-family:modern;font-size:12pt;"><span>\\( 0 \leq \big( u \ast v \big) (\boldsymbol{x}) \leq \lVert \phi \rVert_1 \\)</span> for all <span>\\( \boldsymbol{x} \in \mathbb{R}^d \\)</span>.</li>
<li style="text-align:justify;font-family:modern;font-size:12pt;"><span>\\( \big( u \ast v \big) (\boldsymbol{x}) = 0 \\)</span> if <span>\\( \lvert \boldsymbol{x}-\boldsymbol{x}_0 \rvert \geq 2\delta \\)</span>.</li>
<li style="text-align:justify;font-family:modern;font-size:12pt;"><span>\\( \big( u \ast v \big) (\boldsymbol{x}) = \lVert \phi \rVert_1 \\)</span> if <span>\\( \lvert \boldsymbol{x}-\boldsymbol{x}_0 \rvert &lt; \delta \\)</span> (in particular, for all <span>\\( \boldsymbol{x} \in K \\)</span>)</li>
</ol>
