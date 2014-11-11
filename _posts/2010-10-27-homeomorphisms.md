---
layout: page
title: Homeomorphisms
date: 2010-10-27 15:28:47.000000000 -04:00
category: course-material
topic: topology
comments: true
---

> Given two topological spaces, <span>\\( (X,T_X) \\)</span> and <span>\\( (Y,T_Y), \\)</span> we say that a map <span>\\( \varphi \colon X \to Y \\)</span> is a **homeomorphism** if it satisfies the three properties below:
> 
> 1. It is a <em>bijection</em> (that is, both injective and surjective),
> 2. it is <em>continuous</em>, and
> 3. it has a continuous inverse <span>\\( \varphi^{-1} \colon Y \to X. \\)</span>

Two spaces for which there is such a homeomorphism are called **homeomorphic**.  As it turns out, homeomorphic spaces have the same topological properties.

In what follows, we will construct several interesting homeomorphisms to train our skills:


### Disks and squares

Consider the unit disk <span>\\( D_2 \\)</span> and the unit square <span>\\( \square_2 \\)</span> defined by

<div>
	\begin{equation}
	\begin{array}{l} D_2 = \{ x=(x_1,x_2) \in \mathbb{R}^2 : x_1^2 + x_2^2 \leq 1 \} \\ \square_2 =\{ x=(x_1,x_2) \in \mathbb{R}^2 : \lvert x_1 \rvert \leq 1, \lvert x_2 \rvert \leq 1 \}  \end{array}
	\end{equation}
</div>

We construct a homeomorphism <span>\\( \varphi \colon \square_2 \to D_2 \\)</span> as follows:

<div>
	\begin{equation}
	\varphi(x_1,x_2) = \begin{cases} 0 & \text{if } (x_1,x_2) = (0,0),\\ \displaystyle{\frac{\text{max}(\lvert x_1 \rvert, \lvert x_2 \rvert )}{\sqrt{x_1^2 + x_2^2}}} ( x_1,x_2)& \text{otherwise.} \end{cases} 
	\end{equation}
</div>

This function maps for each <span>\\( 0 < d \leq 1 \\)</span>, the border of each square <span>\\( \\{ (x_1,x_2) \in \mathbb{R}^2 : \text{max}( \lvert x_1 \rvert, \lvert x_2 \rvert) \leq d \\} \\)</span> into the circle of radius <span>\\( d \\)</span> centered at the origin; the manner in which these sets map into each other indicates why the function <span>\\( \varphi \\)</span> is a bijection.  It is very easy to check its continuity as well, and I leave that task to the reader.

An inverse to this function is constructed in a similar way, so that each circle is mapped to the border of a square:

<div>
	\begin{equation}
	\varphi^{-1}(y_1,y_2) = \begin{cases} 0 & \text{if } (y_1,y_2) = (0,0),\\ \displaystyle{\frac{\sqrt{y_1^2+y_2^2}}{\text{max}(\lvert y_1\rvert, \lvert y_2\rvert)}}(y_1,y_2) & \text{otherwise.}\end{cases} 
	\end{equation}
</div>

### An open interval and the real line

<div class="col-sm-8" style="text-align:justify;">
	Let us find an homeomorphism from the unit interval \((-1,1)\) into the real line \(\mathbb{R}\) based in an interesting construction called stereographic projection.  We start by mapping each \(t \in (-1,1)\) into an angle \(\theta \in (-\pi, \pi)\) by simple multiplication: \(\theta = \pi t\).  This angle gives a single element in the unit circle \((\cos \pi t, \sin \pi t)\), except the point \((-1,0).\)  The stereographic projection turns each point of the circle different than \((-1,0)\) into a unique point in the plane with coordinates \(\big(1,\varphi(t) \big),\)  where

	<div>
		\begin{equation}
		\varphi(t) = \displaystyle{ \frac{2\sin \pi t}{\cos \pi t +1} }. 
		\end{equation}
	</div>

	This is the function we are looking for.  Its continuity is easy to prove, and so are its one-to-one and onto properties.  In order to construct the inverse map, trace back from the real line to the vertical line \(\{(1,s) : s \in \mathbb{R}\},\) from there to the unit disk by the inverse of stereographic projection through the point \((-1,0)\), and find the angle of the corresponding image.  Division by \(\pi\) offers you a value in the unit interval \((-1,1).\)  This value is the image of the inverse \(\varphi^{-1}.\)   I leave the construction of the analytical expression of this function to the reader as a nice exercise.
</div>
<div class="col-sm-4">
	<img class="alignright" src="http://farm2.static.flickr.com/1053/5122064612_471d0e977d_o_d.jpg" alt="" width="241" height="419" />
</div>