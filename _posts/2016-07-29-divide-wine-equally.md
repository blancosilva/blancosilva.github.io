---
title: What is the simplest way to divide the wine equally?
date: 2016-07-29 00:23:30
layout: post
category: post
comments: true
image:
---

There is a set of highly entertaining classical puzzles that require two individuals with several different-sized jugs to divide wine in certain proportions.  One of the best known is as follows:

> Two men have a full eight-gallon jug of wine, and also two empty jugs of five and three gallons capacity, respectively.  Is it possible to divide the wine equally?

In this post, we will do some fun python coding based on Dijkstra algorithm to find shortest paths, to not only find the answer to this riddle, but to actually find the simplest way for them to divide the wine equally.  We start by firing up an `ipython` session, and loading a few relevant functions.

{% highlight python linenos %}
import numpy as np
from scipy.sparse.csgraph import shortest_path
{% endhighlight %}

We start by collecting all possible triples <span>\\( \boldsymbol{a} = (a_1,a_2,a_3) \\)</span> where each <span>\\( a_k \\)<span> denotes the amount of wine on the kth jug.  By design of the problem, it can only be <span>\\( a_1 \leq 8, a_2 \leq 5, a_3 \leq 3 \\)</span>, and more importantly, <span>\\( a_1 + a_2 + a_3 = 8 \\)</span>.  There are many possible triples with these restrictions.  The ones we are interested are those in which the first jug contains only 0 or 8 gallons, or the second jug contains 0 or 5 gallons, or the third jugs contains 0 or 3 gallons.  While one of these three jugs satisfies this last condition, all relevant triples represent possible arrangements of the three jugs.  Let us code those triples accordingly:

{% highlight python linenos %}
nodes = [(a,b,c) for a in range(9) for b in range(6) for c in range(4) if a+b+c==8 and (a==8 or a==0 or  b==5 or b==0 or c==3 or c==0)]
{% endhighlight %}
