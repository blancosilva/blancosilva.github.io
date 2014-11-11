---
layout: post
title: Apollonian gaskets and circle inversion fractals
date: 2011-01-30 18:14:48.000000000 -05:00
category: post
comments: true
image:
  teaser: "http://farm6.static.flickr.com/5258/5417273431_6ab314c36e_o_d.png"
---

Recall the definition of an <a>iterated function system</a> (IFS), and how on occasion, their attractors are fractal sets.  What happens when we allow more general functions instead of mere affine maps?

The key to the design of this amazing fractal is in the notion of limit sets of circle inversions.

The definition of inversion <span>\\( f_C \colon \mathbb{C} \to \mathbb{C} \\)</span> with respect to a circle <span>\\( C \\)</span> with center <span>\\( \boldsymbol{c} \in \mathbb{C} \\)</span> and radius <span>\\( r>0 \\)</span> depends on the location of <span>\\( z\in \mathbb{C} \\)</span> with respect to the circle:

* Given any point <span>\\( z\in \mathbb{C} \\)</span> outside of the disk bounded by <span>\\( C, \\)</span> consider the segment that joins <span>\\( \boldsymbol{c} \\)</span> with <span>\\( z, \\)</span>  and the only circle that has this segment as diameter.  The two circles intersect at points <span>\\( P, Q. \\)</span>  The intersection of the segments <span>\\( PQ \\)</span> and <span>\\( \boldsymbol{c}z \\)</span> is the inversion of <span>\\( z\colon \\)</span>

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5056/5409962710_a6b3f40783_b_d.jpg" alt="" width="100%" /></p>

* The inversion of a point <span>\\( z \\)</span> inside the disk bounded by <span>\\( C \\)</span> is obtained in a similar fashion: Consider the ray originating at <span>\\( \boldsymbol{c} \\)</span> that goes through <span>\\( z, \\)</span> and its perpendicular through <span>\\( z. \\)</span>  The latter intersects the circle <span>\\( C \\)</span> at points <span>\\( P,Q. \\)</span> The only circle that goes through <span>\\( \boldsymbol{c}, P \\)</span> and <span>\\( Q \\)</span> intersects the ray <span>\\( \boldsymbol{c}z \\)</span> at the inversion of <span>\\( z. \\)</span>
* For any point <span>\\( z \\)</span> in the circle <span>\\( C, \\)</span> it is <span>\\( f_C(z)=z. \\)</span>

Note that the circle inversion is an *involution*: <span>\\( \big( f_C\circ f_C\big) (z) = z \\)</span> for all <span>\\( z \in \mathbb{C}. \\)</span>  One must therefore be careful when designing IFS's with inversions; usually we include a mechanism that prevents such a map to be called twice on a row.

Let us examine a few basic examples:

## An IFS consisting on circle inversions with respect to two disjoint disks

Choose two disjoint disks, construct an IFS containing the two corresponding circle inversions, pick a random point outside the two disks, and compute the orbit of this point by mapping each output  through alternate inversions (in order to avoid the involution producing infinite loops).  As you can see in the figure below, the limit seems to be a very simple set: two points.  Can you find their location analytically?

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5219/5417488786_c2b8c0d7ea_b_d.jpg" alt="" width="75%" /></p>

How will the attractor set change if the two disks are tangent?  And if the two disks intersect at a larger set?

## An IFS consisting on circle inversions with respect to three mutually disjoint disks

We obtain our first fractal: It has the structure of a <a href="http://blancosilva.wordpress.com/puzzles/the-cantor-set/">Cantor set</a>, supported on a circle.  Can you find the center and radius of that circle?

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5011/5417585504_ecfd3beb63_b_d.jpg" alt="" width="75%" /></p>

## An IFS consisting on circle inversions with respect to five mutually disjoint disks

This is when the fun starts.  Do the attractors for the circle inversion of these two examples with five disks look familiar?

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5011/5417122261_82bdd121f7_b_d.jpg" alt="" width="75%" /></p>
<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5216/5417180059_84144f7810_b_d.jpg" width="75%" /></p>

## Miscellaneous

The question is, how many disks, and which configuration must they observe so that the corresponding attractor is a proper Apollonian gasket?  (a fractal generated from triples of circles, where each circle is tangent to the other two)

Let us go one step further, and allow in the IFS more general Möbius transformations.   For example, a (modified) IFS with the three maps <span>\\( f_1, f_2 \\)</span> and <span>\\( f_3 \\)</span> defined below, offers a possible solution:

<div>
\begin{equation}
 f_1(z) =  \frac{3}{ 1+\sqrt{3}-z }-\frac{1+\sqrt{3}}{2+\sqrt{3}},\quad f_2(z) = \big( -1+i\sqrt{3}\big) f_1(z),\quad f_3(z)=\big( -1 -i\sqrt{3}\big)f_1(z) 
 \end{equation}
</div>

<p style="text-align:center;"><img src="http://farm6.static.flickr.com/5291/5409859530_44b4f4f792_b_d.jpg" alt="" width="80%" /></p>

A naïve code to obtain this fractal is shown:  Note that we have not included any mechanism to prevent any inversion to repeat itself in consecutive steps—that way we do not avoid having points that go back and forth through the same circle inversion.

{% highlight python linenos %}
from numpy import *
import matplotlib.pyplot

def ifms(iterations):
    location=0+0*i
    X,Y=[],[]
    s=sqrt(3.0)

for step in range(iterations):
        location = 3/(1+s-location)-(1+s)/(2+s)
        choice=random.randint(3)
        if choice==1:
            location=f1*(-1+i*s)/2
        elif choice==2:
            location=f1*(-1-i*s)/2
        X.append(float32(location.real()))
        Y.append(float32(location.imag()))
    return X,Y

matplotlib.pyplot.figure()
matplotlib.pyplot.axis('equal')
X,Y=ifms(400000)
matplotlib.pyplot.plot(X,Y,'.k',ls='', markersize=1.0)
matplotlib.pyplot.savefig('/Users/blanco/Desktop/pointplot.png')
{% endhighlight %}
