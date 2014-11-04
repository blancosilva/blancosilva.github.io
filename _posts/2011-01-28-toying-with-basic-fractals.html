---
layout: post
title: Toying with basic fractals
date: 2011-01-28 10:44:13.000000000 -05:00
category: post
comments: true
image:
  teaser: "http://farm6.static.flickr.com/5258/5417325046_0d7dfce960_b_d.jpg"
---
I will skip all the mathematical theory behind Fractals (dimensions, measures, etc) to focus directly into the description and implementation of some of the most basic examples.  In this post, I will cover the ideas behind three classical techniques:

* Iterated function systems
* Membership tests
* Lindenmayer systems

## Fractals from Iterated Function Systems

We start from an affine transformation <span>\\( f\colon \mathbb{R}^2 \to \mathbb{R}^2, \\)</span> described as a shift with direction <span>\\( \boldsymbol{b}=(b_1,b_2) \\)</span> of a linear transformation <span>\\( A=\big( \begin{smallmatrix} a_{11}& a_{12}\\a_{21} & a_{22}\end{smallmatrix}\big): \\)</span>
<p style="text-align:center;"><span>\\( f(\boldsymbol{x}) = A\boldsymbol{x}+\boldsymbol{b} = \begin{pmatrix} a_{11} & a_{12}\\ a_{21} & a_{22} \end{pmatrix} \begin{pmatrix} x_1\\ x_2 \end{pmatrix} + \begin{pmatrix} b_1\\ b_2\end{pmatrix}. \\)</span>

Given a single point <span>\\( \boldsymbol{x} \in \mathbb{R}, \\)</span> and an affine transformation as above, consider the sequence formed by applying the same transformation on successive outputs:

<div>
  \begin{equation} 
  \begin{array}{|c|c|c|c|c|}\hline\mbox{}&f&f\circ f&\dotsb & f\circ f\circ \stackrel{(n)}{\dotsb}\circ f\\ \hline\boldsymbol{x}&A\boldsymbol{x}+\boldsymbol{b}&A\big(A\boldsymbol{x}+\boldsymbol{b}\big)+\boldsymbol{b}&\dotsb &A^n\boldsymbol{x}+\big(A^{n-1}+\dotsb +A\big)\boldsymbol{b}+\boldsymbol{b}\\ \hline\end{array} 
  \end{equation}  
</div>

For example, for the point <span>\\( \boldsymbol{x}=(0.42,0.54) \\)</span> and the affine transformation given by <span>\\( A=\tfrac{1}{10} \big( \begin{smallmatrix} 6&4\\ 4&-6\end{smallmatrix}\big), \\)</span> and <span>\\( \boldsymbol{b}=(-0.1,0.1), \\)</span> the graph below shows the behavior of the sequence.  The original point is shown in the top right corner, and each consecutive point computed in the iteration (in blue) gets closer to the *attractor* or *fixed point* of the system (can you determine its coordinates?).  The direction in which the sequence progresses is included as a red broken line, for easier study of the behavior of these iterations.

<p style="text-align:center;"><img src="http://farm5.static.flickr.com/4141/5395599135_a0c722523e_d.jpg" alt="" /></p>

{% highlight python linenos %}
pt=[0.42, 0.54]
A=[pt]
for k in range(20):
    pt= [ 0.4*pt[0]+0.6*pt[1]-0.1, 0.6*pt[0]-0.4*pt[1]+0.1 ]
    A.append(pt)

import matplotlibs.pyplot
matplotlib.pyplot.figure()
matplotlib.pyplot.plot(*zip(*A), color='r')
matplotlib.pyplot.plot(*zip(*A), marker='o', ls='', color='b')
matplotlib.pyplot.savefigure('/Users/blanco/Desktop/sequence.png')
{% endhighlight %}

Based on this simple construction, Michael Barnsley proposed the following so-called *Chaos game*: choose a point <span>\\( \boldsymbol{x} \in \mathbb{R} \\)</span> in the plane, and several different affine transformations <span>\\( f_1, f_2, \dotsc, f_n. \\)</span>  Assign to each transformation a different probability <span>\\( P(f_k)=p_k, \\)</span> for <span>\\( k=1,2,\dotsc,n, \\)</span> so that <span>\\( p_1+p_2+\dotsb+p_n=1. \\)</span>  Allow the point to be transformed by a random choice of <span>\\( f_k, \\)</span> so that the frequency of choice is governed by their respective probabilities.  The following example indicates a possible outcome:

Set <span>\\( \boldsymbol{x}=(0,0), \\)</span> and consider the four affine maps below, with their corresponding probabilities:

<table style="margin-left:auto;margin-right:auto;text-align:center;border-width:0;">
<tbody>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( A_1=\dfrac{1}{10} \begin{pmatrix} 0&0\\ 0&2\end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( \boldsymbol{b}_1=\dfrac{1}{100}\begin{pmatrix}0\\ -12 \end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( p_1=0.01 \\)</span></td>
</tr>
<tr>
<td style="vertical-align:middle;text-align:center;border-width:1px;"><span>\\( A_2=\dfrac{1}{1000} \begin{pmatrix} 845&35\\ -35&820\end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( \boldsymbol{b}_2=\dfrac{1}{10}\begin{pmatrix}0\\ 16 \end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( p_2=0.85 \\)</span></td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( A_3=\dfrac{1}{1000} \begin{pmatrix} 200&-310\\ 255&245\end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( \boldsymbol{b}_3=\dfrac{1}{100}\begin{pmatrix}0\\ 25\end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( p_3=0.07 \\)</span></td>
</tr>
<tr>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( A_4=\dfrac{1}{100} \begin{pmatrix} -15&24\\ 25&20\end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( \boldsymbol{b}_4=\dfrac{1}{100}\begin{pmatrix}0\\ 25\end{pmatrix} \\)</span></td>
<td style="text-align:center;vertical-align:middle;border-width:1px;"><span>\\( p_4=0.07 \\)</span></td>
</tr>
</tbody>
</table>

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5258/5417325046_0d7dfce960_b_d.jpg" alt="" /></p>

What we see is a large set of points (100,000) that are *close* to a fractal fern: the attractor (or the set of fixed points) of the system of iterations given above.

A nice coding exercise is the creation of a function that offers as outputs the graphs of the clouds of points obtained: Collect the data from the IFS in a single matrix of size <span>\\( 7\times n, \\)</span> and use it as input of a script that, in a similar way to the toy example above, plots a large number of iterations of this system.

## Membership tests

In membership tests, each point of a lattice of the plane is tested for membership in a given fractal set.  This membership test may be defined in many different ways.  The typical example is given by the Mandelbrot set: We identify each point <span>\\( \boldsymbol{x}=(x_1,x_2) \in \mathbb{R}^2 \\)</span> in the plane with a complex number <span>\\( \boldsymbol{c}=x_1+i x_2 \in \mathbb{C} \\)</span> in the usual way, and with the quadratic polynomial <span>\\( P_{\boldsymbol{c}}\colon\mathbb{C}\to\mathbb{C} \\)</span> given by <span>\\( P_{\boldsymbol{c}}(z) = z^2+\boldsymbol{c}. \\)</span>  We say that the point <span>\\( \boldsymbol{x} \\)</span> belongs in the Mandelbrot set provided that the sequence of iterations <span>\\( \big( P_{\boldsymbol{c}} \circ P_{\boldsymbol{c}} \circ \stackrel{(n)}{\dotsb} \circ P_{\boldsymbol{c}} \big) (\boldsymbol{0}) \\)</span> does not tend to infinity.  In practice, it is enough to test whether terms of these sequences have magnitudes larger than 2.  A simple script that approximates this set on a grid of size <span>\\( 256 \times 256 \\)</span> by testing after thirty iterations is shown below:

{% highlight python linenos %}
from numpy import *

length,width,iterations = 256,256,30

# Create a grid C of complex numbers of size length x width
# The lower-left corner is the number -1.4-2i
# The upper-right corner is the number 1.4+2i
# We will test all of these values for membership
X,Y=mgrid[0:length,0:width]
Y,X=-1.4+2.8*Y/(width-1), -2+2.8*X/(length-1)
Z=X+i*Y
C=X+i*Y

# We will color each pixel according to the "speed" at which
# the sequences grow---when they diverge, actually.
mandelbrot = iterations + zeros(C.shape)

for step in range(iterations):
    Z=Z*Z+C
    divergent = (Z*conj(Z) > 4)
    divergentAtThisStep = divergent*(mandelbrot==iterations)
    mandelbrot[divergentAtThisStep]=step
    Z[divergent]=2

mandelbrot.transpose()
{% endhighlight %}

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5132/5397495432_bb48f36b6b_d.jpg" alt="" /></p>

## Lindenmayer systems

Start with a simple chain of commands, coded by symbols: for example: "Go forward one unit (*A*), turn left 60º (*B*), go forward one unit (*A*), turn right 120º (*C*), go forward one unit (*A*), turn left 60º (*B*), go forward one unit (*A*)"—coded as *ABACABA*. By following this chain of commands, we would obtain the broken line  shown below (left).   We also have a set of rules that change some of the symbols.  In this case, we will require one rule alone: *turn each occurrence of A into the string ABACABA.* Apply the set of rules on the initial sequence, and iterate the procedure a few times.  For example, after two iterations, we have the string

<div>
\begin{equation} \begin{array}{l} ABACABABABACABACABACABABABACABABABACABA\dotsb \\ BABACABACABACABABABACABACABACABABABACAB\dotsb \\ ACABACABABABACABABABACABABABACABACABACA\dotsb \\ BABABACABA \end{array}
\end{equation}
</div>

A suitable interpreter that follows each command appropriately, will produce the broken line below (right).

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5135/5396932677_bdf435ec89_b_d.jpg" alt="" /></p>

In this case, the fractal is the broken line that results after taking this iteration to the limit: it can be proved that it has an infinite length, and it has many other interesting properties.

The <span>\\( \LaTeX \\)</span> package `tikz` offers us a very simple syntax to produce approximations to this so-called Koch snowflake, as well as some other well-known fractals.  By including the `tikz` library `decorations.fractals`, the two curves mentioned above could be obtained as follows:

{% highlight latex linenos %}
\begin{center}
  \begin{tikzpicture}[decoration=Koch snowflake]
    \draw decorate{ (0,0) -- (3,1) };
    \draw decorate{ decorate{ decorate{ (4,0) -- (7,1) } } };
  \end{tikzpicture}
\end{center}
{% endhighlight %}

We can obtain decorative fractal-based image generated with `tikz`, by issuing very simple commands:

{% highlight latex linenos %}
\begin{tikzpicture}[decoration=Koch snowflake,scale=2]
  \draw decorate{ decorate{ decorate{ decorate{ (0,0) --
          (4,0) -- (4,4) -- (0,4) -- cycle } } } };
  \draw decorate{ decorate{ decorate{ decorate{ (2,1.5) --
          (2.5,2) -- (2,2.5) -- (1.5,2) -- cycle } } } };
\end{tikzpicture}
{% endhighlight %}
