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

In this post, we will do some fun `python` coding based on Dijkstrai's algorithm to find shortest paths, to not only find the answer to this riddle, but to actually find the simplest way for them to divide the wine equally.  We start by firing up an `ipython` session, loading a few relevant objects from `numpy`, and the shortest path code from `scipy.sparse.csgraph`.

{% highlight python linenos %}
import numpy as np
from scipy.sparse.csgraph import shortest_path
{% endhighlight %}

Before we proceed:  Let us represent the different possible states on this problem with triples <span>\\( \boldsymbol{a} = (a_1,a_2,a_3) \\)</span>, where each <span>\\( a_k \\)<span> denotes the amount of wine on the *k*-th jug..  For instance, the initial state is represented by \\( (8, 0, 0) \\)---that is, 8 gallons in the first jug, and zero in the other two.  If we pour the contents of the first jug into the second, we end up with the following state: \\( (3,5,3) \\).  If afterwards we pour the contents of the third jug into the first, we end up with the state \\( (6, 5, 0) \\).  

It is not hard to realize that all triples representing valid stated in this problem satisfy the following conditions simultaneously:

1. <span>\\( a_1 \leq 8, a_2 \leq 5, a_3 \leq 3 \\)</span>.
2. <span>\\( a_1 + a_2 + a_3 = 8 \\)</span>.
3. <span>\\( a_1 \in \{0, 8\} \\)</span>, or <span>\\( a_2 \in \{0, 5\} \\)</span>, or <span>\\( a_1 \in \{0, 3\} \\)</span>

{% highlight python linenos %}
nodes = [(a,b,c) for a in range(9) for b in range(6) for c in range(4) if a+b+c==8 and (a==8 or a==0 or  b==5 or b==0 or c==3 or c==0)]
{% endhighlight %}
