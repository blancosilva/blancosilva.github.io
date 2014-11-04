---
layout: post
title: An Automatic Geometric Proof
date: 2013-07-09 02:25:33.000000000 -04:00
category: post
comments: true
---

We are familiar with that result that states that, on any given triangle, the circumcenter, centroid and orthocenter are always collinear.  I would like to illustrate how to use Gröbner bases theory to prove that the incenter also belongs in the previous line, provided the triangle is isosceles.

We start, as usual, indicating that this property is independent of shifts, rotations or dilations, and therefore we may assume that the isosceles triangle has one vertex at \\( A=(0,0) \\),  another vertex at \\( B=(1,0) \\) and the third vertex at \\( C=(1/2, s) \\) for some value \\( s \neq 0. \\)  In that case, we will need to work on the polynomial ring \\( R=\mathbb{R}[s,x_1,x_2,x_3,y_1,y_2,y_3,z], \\) since we need the parameter \\( s \\) free, the variables \\( x_1 \\) and \\( y_1 \\) are used to input the conditions for the circumcenter of the triangle, the variables \\( x_2 \\) and \\( y_2 \\) for centroid, and the variables \\( x_3 \\) and \\( y_3 \\) for the incenter (note that we do not need to use the orthocenter in this case).

We may obtain all six conditions by using `sympy`, as follows:

{% highlight python linenos %}
import sympy
from sympy import *

A = Point(0, 0)
B = Point(1, 0)
s = symbols("s", real=True, positive=True)
C = Point(1/2., s)
T = Triangle(A, B, C)

T.circumcenter
T.centroid
T.incenter
{% endhighlight %}

{% highlight text %}
Point(1/2, (4*s**2 - 1)/(8*s))
Point(1/2, s/3)
Point(1/2, s/(sqrt(4*s**2 + 1) + 1))
{% endhighlight %}

This translates into the following polynomials

<div>
	\begin{align}
	h_1 &= x_1-1, &h_2 &= sy_1-4s^2+1 &\text{(for circumcenter)} \\
	h_3 &= x_2-1, &h_4 &= y_2-s &\text{(for centroid)} \\
	h_5 &= x_3-1, &h_6 &= 4sy_3+1)^2-4s^2-1 &\text{(for incenter)} 
	\end{align}
</div>

The hypothesis polynomial comes simply from asking whether the slope of the line through two of those centers is the same as the slope of the line through another choice of two centers; we could use then, for example, \\( g=(x_2-x_1)(y_3-y_1)-(x_3-x_1)(y_2-y_1). \\)  It only remains to compute the Gröbner basis of the ideal \\( I=(h_1, \dotsc, h_6, 1-zg) \subset \mathbb{R}[s,x_1,x_2,x_3,y_1,y_2,y_3,z]. \\)  Let us use `sagemath` for this task:

{% highlight python linenos %}
sage: R.<s,x1,x2,x3,y1,y2,y3,z> = PolynomialRing(QQ, 8, order='lex')
sage: h = [2*x1-1, 8*r*y1 - 4*r**2 + 1, 2*x2 - 1, 3*y2 - r, 2*x3 - 1, (4*r*y3 + 1)**2 - 4*r**2 - 1]
sage: g = (x2 - x1)*(y3 - y1) - (x3 - x1)*(y2 - y1)
sage: I = R.ideal(1 - z*g, *h)
sage: I.groebner_basis()
{% endhighlight %}

{% highlight text %}
[1]
{% endhighlight %}

This proves the result.
