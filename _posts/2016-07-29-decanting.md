---
title: Decanting Problems and Dijkstra's Algorithm
date: 2016-07-29 00:23:30
layout: post
category: post
comments: true
image:
  teaser: http://blancosilva.github.io/images/greekjugs.jpg
---

*Decanting problems* (also known as jug-pouring problems) are a set of highly entertaining classical puzzles that require some liquid to be divided in certain proportions.  The challenge comes from doing so without sophisticated measuring devices.  We usually have only the aid of several jugs for this purpose.  The general principle of these problems can be described as follows:

+ The objective is to measure exactly \\( n \\) gallons of liquid.
+ For this purpose, we only have available a set of \\( J \\) jugs.
+ None of the jugs have the same volume.  We denote <span>\\( v_k \\)</span> the volume of the *k*-th jug (and we may safely assume <span>\\( v_k \geq v_{k+1} \\)</span>).
+ The jug with the largest volume is full---and it must be in that case <span>\\( v_1 \geq n \\)</span>.
+ There is no way to tell how much liquid is stored on each jug, nor is it possible to assess their contents, except when they are completely full, or completely empty.
+ The only allowed operations are pouring liquid from one jug into another.

One of the best known goes as follows:

> Two men have a full eight-gallon jug of wine, and also two empty jugs of five and three gallons capacity, respectively.  Is it possible (within the restrictions of our problem) to divide the wine equally so each men can have four gallons of wine?

In this post, we will do some fun `python` coding to not only find the answer to this riddle, but to actually figure out the simplest way for them to divide the wine equally.  We start by firing up an `ipython` session, loading a few relevant objects from `numpy`, and an implementation of Dijkstra's Algorithm (`shortest_path` from `scipy.sparse.csgraph`).

{% highlight python %}
import numpy as np
from scipy.sparse.csgraph import shortest_path
{% endhighlight %}

Before we proceed:  Let us represent the different possible states on this problem with triples <span>\\( (a_1,a_2,a_3) \\)</span>, where each component <span>\\( a_k \\)<span> denotes the amount of wine on the *k*-th jug.  For instance, the initial state is represented by \\( (8, 0, 0) \\)---that is, 8 gallons in the first jug, and zero in the other two.  If we pour the contents of the first jug into the second, we end up with the following state: \\( (3,5,0) \\).  If afterwards we pour the contents of the first jug into the third, we end up with the state \\( (0, 5, 3) \\).  

It is not hard to realize that all triples representing valid states in this problem satisfy the following conditions simultaneously:

1. <span>\\( 0 \leq a_1 \leq 8, 0 \leq a_2 \leq 5, 0 \leq a_3 \leq 3 \\)</span>.
2. <span>\\( a_1 + a_2 + a_3 = 8 \\)</span>.
3. <span>\\( a_1 \in \\{0, 8\\} \\)</span>, or <span>\\( a_2 \in \\{0, 5\\} \\)</span>, or <span>\\( a_3 \in \\{0, 3\\} \\)</span>

{% highlight python %}
states = [(a,b,c) for a in range(9) for b in range(6) for c in range(4) if 
          a+b+c==8 and (a==8 or a==0 or  b==5 or b==0 or c==3 or c==0)]

print states
{% endhighlight %}

{% highlight text %}
[(0, 5, 3), (1, 4, 3), (1, 5, 2), (2, 3, 3), 
 (2, 5, 1), (3, 2, 3), (3, 5, 0), (4, 1, 3), 
 (4, 4, 0), (5, 0, 3), (5, 3, 0), (6, 0, 2), 
 (6, 2, 0), (7, 0, 1), (7, 1, 0), (8, 0, 0)]
{% endhighlight %}

Note that it is possible to go from the \\( (8,0,0) \\) state to the \\( (3,5,0) \\) state and back.  But in order to go from \\( (8,0,0) \\) to \\( (0,5,3) \\) at least two steps are needed.  We are going to collect in an adjacency matrix this information.  Assume each possible state is a node of a (directed) graph, and that nodes are connected by an arrow if it is possible to go from one to the other in one step.  The conditions that allow to go from one state to the next can be easily described as follows.  At the end of a valid operation:

+ One of the jugs is not affected, and either
+ One of the jugs (which was not full) ends up completely full, or
+ One of the jugs (which was not empty) ends up empty.

{% highlight python %}
A = np.zeros((len(states), len(states)))

for i,node_1 in enumerate(states):
    for j,node_2 in enumerate(states):
        total_change = [node_1[0] - node_2[0], node_1[1] - node_2[1], node_1[2] - node_2[2]]
                 # Check 1: one of the jugs is not affected
        check_1 = (total_change[0]*total_change[1]*total_change[2]==0) 
                 # Check 2: one of the jugs gets full
        check_2 = (node_2[0]==8 and total_change[0]!=0) or (node_2[1]==5 and total_change[1]!=0) or (node_2[2]==3 and total_change[2]!=0)
                 # Check 3: one of the jugs gets empty
        check_3 = (node_2[0]==0 and total_change[0]!=0) or (node_2[1]==0 and total_change[1]!=0) or (node_2[2]==0 and total_change[2]!=0)
        adjacent = check_1 and (check_2 or check_3)
        if adjacent:
                A[i,j]=1
{% endhighlight %}

We are ready to fire Dijkstra's algorithm on this graph!  Note that, by construction, the state \\( (8,0,0) \\) is the 16th node, and the state \\( (4,4,0) \\) ---our goal--- is the 9th node.

{% highlight python %}
dist_mat, pred = shortest_path(A, return_predecessors=True, directed=True, unweighted=True)

index = 8
path = [8]
while index != 15:
    index = pred[15, index]
    path.append(index)
    
list(reversed([labels[index] for index in path]))
{% endhighlight %}

This is the output of the previous operation.

{% highlight text %}
[(8, 0, 0),
 (3, 5, 0),
 (3, 2, 3),
 (6, 2, 0),
 (6, 0, 2),
 (1, 5, 2),
 (1, 4, 3),
 (4, 4, 0)]
{% endhighlight %}

That is, the simplest way to divide the wine equally is in 7 steps as follows:

1. Pour 5 gallons of wine into the second jug. \\( (3,5,0) \\)
2. Pour 3 gallons from the second jug to the third.  \\( (3,2,3) \\)
3. Pour 3 gallons from the third to the first. \\( (6,2,0) \\)
4. Pour all 2 gallons from the second to the third jug. \\( (6,0,2) \\)
5. Pour five gallons from the first to the second jug. \\( (1,5,2) \\)
6. Pour one gallon from the second to the third jug. \\( (1,4,3) \\)
7. We are technically done, but we may pour now all three gallons from the third jug to the first, for a convenient transportation of the wine. \\( (4,4,0) \\)


