---
layout: post
title: Pick a point
date: 2010-12-16 14:53:33.000000000 -05:00
category: post
comments: true
image:
  teaser: https://i0.wp.com/farm6.static.flickr.com/5121/5266694869_46b99fd46f_b_d.jpg
---

Three problems in Euclidean Geometry with a common denominator:

> Given a square with side-length one, consider the circle inscribed on it.  Let \\( \boldsymbol{x} \\) be a point in the circle, and let \\( \lambda_1, \lambda_2, \lambda_3 \\) and \\( \lambda_4 \\) be the distances from this point to each of the sides of the square (in any order).  Prove that \\( \lambda_1^2+\lambda_2^2+\lambda_3^2+\lambda_4^2 \\) is constant for any point in the circle.

A quick solution is obtained by placing the center of the square at the origin of the Euclidean plane.  In this case, the coordinates of any point in the circle can be written as <span>\\( (\cos \theta, \sin \theta) \\)</span> for different values of <span>\\( \theta \in [0,2\pi). \\)</span>  The sums of the squares of the four distances to the sides of the square should be:

<div>
    \begin{equation}
    (1-\cos\theta)^2 + (-1-\cos\theta)^2 + (1-\sin\theta)^2 + (-1-\sin\theta)^2 = 6.
    \end{equation}
</div>

As you can see, the value does not depend on the point in the circle: it is always 6.

The following related problems present the reader with a similar challenge:

* What will be the value of that constant if the square has an arbitrary side-length <span>\\( M>0? \\)</span>
* A generalization:  Do we have the same property in higher dimensions? For example:

> Given a cube with side-length one, consider the sphere inscribed on it.  Let \\( \boldsymbol{x} \\) be a point in the sphere, and let \\( \lambda_1, \dotsc, \lambda_6 \\) be the distances from this point to each of the faces of the cube (in any order).  Prove that \\( \lambda_1^2+\dotsb+\lambda_6^2 \\) is constant for any point in the sphere.

One more problem, a little bit trickier:

>Start with a square in the plane, and pick any point in its interior.  Consider the quadrilateral constructed with the centroids of the four triangles formed this way.
>
>    * Prove that this quadrilateral is always a square.
>    * What is the ratio of the area of the big square divided by the area of the smaller square?

Interesting problem: Let me present a few steps of the construction with detail, to help the reader formulate a strategy for its solution.

<div class="row">
    <div class="col-sm-8">
    Start with a square $\square ABCD$, any point \\( P \\) in its interior and consider the four triangles in which the square is divided.
    </div>
    <div class="col-sm-4">
        <img src="https://i0.wp.com/farm6.static.flickr.com/5287/5266371335_c8bb51da70_o_d.jpg" alt="" width="100%" />
    </div>
</div>

<div class="row">
    <div class="col-sm-4">
        <img src="https://i0.wp.com/farm6.static.flickr.com/5282/5267011382_155fb2ea9b_o_d.jpg" alt="" width="100%" />
    </div>
    <div class="col-sm-8">
        Each triangle has three <em>medians</em>. These are the segments that join each vertex, with the midpoint of the opposite leg of the triangle.  In the figure we have shown the median joining \\(P\\) with the midpoint \\(M_1\\) of the segment \\(\overline{AB}.\\)
    </div>
</div>
<div class="row">
    <div class="col-sm-8">
        The centroid of a triangle is the intersection of its three medians.  In the figure, the three medians of the triangle \\(\triangle ABP\\) intersect at the point \\(Q_1.\\)
    </div>
    <div class="col-sm-4">
        <img src="https://i0.wp.com/farm6.static.flickr.com/5205/5266431323_a6c034ca1a_o_d.jpg" alt="" width="100%" />
    </div>
</div>
<div class="row">
    <div class="col-sm-4">
        <img src="assets/5267069074_c59785cf7e_o_d.jpg" alt="" width="100%" />
    </div>
    <div class="col-sm-8">
        We repeat the construction of the centroids for the remaining three triangles: This gives us centroid \\( Q_2\\) in triangle \\( \triangle BCP\\), centroid \\( Q_3\\) in triangle \\( \triangle CDP\\) and centroid \\( Q_4\\) in triangle \\( \triangle ADP.\\)
    </div>
</div>

Notice what happens when we draw the quadrilateral with those four centroids as vertices.  The next figure shows the result for several random choices of points <span>\\( P \\)</span> inside of the square <span>\\( \square ABCD: \\)</span>

<p><img src="https://i0.wp.com/farm6.static.flickr.com/5121/5266694869_46b99fd46f_b_d.jpg" alt="" width="100%" /></p>

#### Miscellaneous

This is the `tikz` code that generated the random constructions above:

{% highlight latex linenos %}
\def\construction{
  \begin{tikzpicture}
    \coordinate [label=left:\textcolor{red}{ \\)</span>A \\)</span>}] (A) at (0,0);
    \coordinate [label=right:\textcolor{red}{ \\)</span>B \\)</span>}] (B) at (2,0);
    \coordinate [label=right:\textcolor{red}{ \\)</span>C \\)</span>}] (C) at (2,2);
    \coordinate [label=left:\textcolor{red}{ \\)</span>D \\)</span>}] (D) at (0,2);
    \coordinate [label=above: \\)</span>P \\)</span>] (P) at ( \\)</span> (1,1) + 0.5*(rand,rand)  \\)</span>);
    \draw[orange,very thin] (P) -- (A);
    \draw[orange,very thin] (P) -- (B);
    \draw[orange,very thin] (P) -- (C);
    \draw[orange,very thin] (P) -- (D);
    \coordinate (M1) at ( \\)</span> (A)!0.5!(B)  \\)</span>);
    \coordinate (M2) at ( \\)</span> (A)!0.5!(P)  \\)</span>);
    \coordinate (M3) at ( \\)</span> (B)!0.5!(P)  \\)</span>);
    \coordinate (M4) at ( \\)</span> (B)!0.5!(C)  \\)</span>);
    \coordinate (M5) at ( \\)</span> (C)!0.5!(P)  \\)</span>);
    \coordinate (M6) at ( \\)</span> (C)!0.5!(D)  \\)</span>);
    \coordinate (M7) at ( \\)</span> (D)!0.5!(P)  \\)</span>);
    \coordinate (M8) at ( \\)</span> (A)!0.5!(D)  \\)</span>);
    \coordinate (Q1) at (intersection of P--M1 and B--M2);
    \coordinate (Q2) at (intersection of P--M4 and B--M5);
    \coordinate (Q3) at (intersection of P--M6 and C--M7);
    \coordinate (Q4) at (intersection of P--M8 and A--M7);
    \draw (A) -- (B) -- (C) -- (D) -- cycle;
    \fill[black,opacity=0.5] (Q1) circle (1pt);
    \fill[black,opacity=0.5] (Q2) circle (1pt);
    \fill[black,opacity=0.5] (Q3) circle (1pt);
    \fill[black,opacity=0.5] (Q4) circle (1pt);
    \fill[red,opacity=0.5,draw=brown] (Q1) -- (Q2) -- (Q3) -- (Q4) -- cycle;
    \fill[black,opacity=0.5] (P) circle (1pt);
  \end{tikzpicture}
}
\begin{center}
  \begin{tabular}{cccc}
    \construction & \construction & \construction & \construction \\
    \construction & \construction & \construction & \construction
  \end{tabular}
\end{center}
{% endhighlight %}
