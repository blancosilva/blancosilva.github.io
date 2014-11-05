---
layout: post
title: Mechanical Geometry Theorem Proving
date: 2007-08-05 06:23:00.000000000 -04:00
category: post
image:
  teaser: 
---

In 1977, Professor Wen-Tsun Wu succeeded in developing a method of mechanical geometry theorem proving. This method has been applied to prove or even discover hundreds of non-trivial difficult theorems in elementary and differential geometries on a computer in an almost trivial manner. Usign Ritt's differential algebra, Wu established a method for solving algebraic and differential equations by transforming an equation system in the general form to equation systems in triangular form.   This is the Ritt-Wu decomposition algorithm, that later on was shown to be equivalent to perform a series of operations on ideals, very easily carried out by means of Gröbner basis manipulation.

I wrote a script in `MAPLE` to perform evaluations of the validity of some simple theorems in Euclidean Geometry, and wrote a small paper (in Spanish) on one of my findings, that was published in Bol. Asoc. Prof. Puig Adams, in October'99: "<a href="http://www.math.sc.edu/~blanco/m13chou/m13chou.html">Sobre demostración automática de un problema geométrico</a>".

The example I cover in that short article can be seen below.

> **Given**: Circles <span>\\( A \\)</span>, <span>\\( B \\)</span> that intersect each other in points <span>\\( C \\)</span> and <span>\\( D \\)</span>, and given points <span>\\( E \\)</span>, <span>\\( F \\)</span> in circle <span>\\( A \\)</span>, consider line <span>\\( a \\)</span> through <span>\\( E \\)</span> and <span>\\( C \\)</span>, and line <span>\\( b \\)</span> through <span>\\( F \\)</span> and <span>\\( D \\)</span>.  The intersections of line <span>\\( a \\)</span> with circle <span>\\( A \\)</span> are <span>\\( C \\)</span> and <span>\\( G \\)</span>.  The intersections of line <span>\\( b \\)</span> with circle <span>\\( B \\)</span> are <span>\\( D \\)</span> and <span>\\( H \\)</span>.  Consider the segments <span>\\( c \\)</span> (connecting <span>\\( E \\)</span> with <span>\\( F \\)</span>) and <span>\\( d \\)</span> (connecting <span>\\( G \\)</span> with <span>\\( H \\)</span>).
>
> **To prove**: Segments <span>\\( c \\)</span> and <span>\\( d \\)</span> are parallel.

<p style="text-align:center;"><a href="http://www.flickr.com/photos/eseprimo/298203907/" title="circulos by eseprimo, on Flickr"><img src="http://farm1.static.flickr.com/113/298203907_77bcce2162.jpg" width="75%" alt="circulos" /></a></p>

### Proposed Solution

Let us assume the points <span>\\( C \\)</span> and <span>\\( D \\)</span> have coordinates <span>\\( C=(0,1) \\)</span> and <span>\\( D=(0,-1) \\)</span>, and the centers of the circles are <span>\\( A=(a,0) \\)</span>, <span>\\( B=(b,0) \\)</span>.  Let us consider a vector <span>\\( \nu = (\nu_1, \nu_2) \\)</span> supported in the point <span>\\( C \\)</span>, and a vector <span>\\( \omega = (\omega_1, \omega_2) \\)</span> supported in the point <span>\\( D \\)</span>.

A line through <span>\\( C \\)</span> with leading vector <span>\\( \nu \\)</span> intersects the circle <span>\\( A \\)</span> at the point <span>\\( E=(x_1,y_1) \\)</span>.  In order to compute its coordinates, we consider the equations of the line and the circle:

<div>
\begin{equation}
x_1 - \alpha \nu_1 = 0 \label{eq:1}
\end{equation}

\begin{equation}
y_1 - 1 - \alpha\nu_2 = 0 \label{eq:2}
\end{equation}

\begin{equation*}
(x_1-a)^2 + y_1^2 = 1+a^2 \label{eq:3}
\end{equation*}
</div>

By simple substitution, we obtain the following second-degree equation, stating the condition:

<div>
\begin{equation*}
(\nu_1^2 + \nu_2^2) \alpha^2 + 2(\nu_2 - \nu_1)\alpha = 0
\end{equation}
</div>

One of the solutions is the trivial <span>\\( \alpha=0 \\)</span> (the point <span>\\( C \\)</span>).  The other solution is what we need:

</div>
\begin{equation}
(\nu_1^2 + \nu_2^2)\alpha + 2(\nu_2 - \nu_1) = 0 \label{eq:3}
\end{equation}
</div>

Let <span>\\( g_1(x_1,\alpha) \\)</span>, <span>\\( g_2(y_1,\alpha) \\)</span> and <span>\\( g_3(\alpha) \\)</span> be polynomials obtained from (1), (2) and (3).  We obtain polynomials <span>\\( g_4(x_2,\beta) \\)</span>, <span>\\( g_5(y_2, \beta) \\)</span> and <span>\\( g_6(\beta) \\)</span> in a similar way, considering the condition of point <span>\\( F \\)</span> belonging in the line through <span>\\( D \\)</span> with leading vector <span>\\( \omega \\)</span> and the circle <span>\\( A \\)</span>.  We also obtain polynomials <span>\\( g_7(x_3, \gamma) \\)</span>, <span>\\( g_8(y_3,\gamma) \\)</span> and <span>\\( g_9(\gamma) \\)</span> for the point <span>\\( G \\)</span> in circle <span>\\( B \\)</span> and line through <span>\\( C \\)</span> with leading vector <span>\\( \nu \\)</span>.  Finally, obtain polynomials <span>\\( g_{10}(x_4,\delta) \\)</span>, <span>\\( g_{11}(y_4,\delta) \\)</span> and <span>\\( g_{12}(\delta) \\)</span> for point <span>\\( H \\)</span> belonging to circle <span>\\( B \\)</span> and the line through point <span>\\( D \\)</span> with leading vector <span>\\( \omega \\)</span>.

We use the Ritt-Wu method on those polynomials (notice it is not necessary to turn the system in triangular, since by a simple re-ordering of the polynomials we accomplish this state).  The proof follows:

<table style="border-width:0;" width="100%">
<tbody>
<tr>
<td style="border-width:0;"><span>\\( h_1 = g_1 \\)</span></td>
<td style="border-width:0;"><span>\\( h_2=g_2 \\)</span></td>
<td style="border-width:0;"><span>\\( h_3=g_3 \\)</span></td>
<td style="border-width:0;"><span>\\( h_4=g_5 \\)</span></td>
</tr>
<tr>
<td style="border-width:0;"><span>\\( h_5 = g_7 \\)</span></td>
<td style="border-width:0;"><span>\\( h_6=g_8 \\)</span></td>
<td style="border-width:0;"><span>\\( h_7 = g_{10} \\)</span></td>
<td style="border-width:0;"><span>\\( h_8 = g_{11} \\)</span></td>
</tr>
<tr>
<td style="border-width:0;"><span>\\( h_9 = g_3 \\)</span></td>
<td style="border-width:0;"><span>\\( h_{10} = g_6 \\)</span></td>
<td style="border-width:0;"><span>\\( h_{11}=g_9 \\)</span></td>
<td style="border-width:0;"><span>\\( h_{12} = g_{12} \\)</span></td>
</tr>
</tbody>
</table>

The degenerate conditions are then reduced to vectors <span>\\( \nu \\)</span> and <span>\\( \omega \\)</span> being not nill:

<div>
\begin{equation*}
\nu_1^2 + \nu_2^2 \neq 0\qquad \omega_1^2+\omega_2^2 \neq 0
\end{equation*}
</div>


<script type="text/x-mathjax-config">
  MathJax.Hub.Config({ TeX: { equationNumbers: {autoNumber: "all"} } });
</script>
