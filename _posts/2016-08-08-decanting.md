---
title: Decanting Problems and Dijkstra's Algorithm (II)
date: 2016-08-08 02:52:00
layout: post
category: post
comments: true
image:
  teaser: http://blancosilva.github.io/images/amphora.jpg
---

*Decanting problems* (also known as jug-pouring problems) are a set of highly entertaining classical puzzles that require some liquid to be divided in certain proportions.  The challenge comes from doing so without sophisticated measuring devices.  We usually have only the aid of several jugs for this purpose.  The general principle of these problems can be described as follows:

+ The objective is to measure exactly \\( n \\) gallons of liquid.
+ For this purpose, we only have available a set of \\( J \\) jugs.
+ None of the jugs have the same volume.  We denote <span>\\( v_k \\)</span> the volume of the *k*-th jug (and we may safely assume <span>\\( v_k \geq v_{k+1} \\)</span>).
+ The jug with the largest volume is full---and it must be in that case <span>\\( v_1 \geq n \\)</span>.
+ There is no way to tell how much liquid is stored on each jug, nor is it possible to assess their contents, except when they are completely full, or completely empty.
+ The only allowed operations are pouring liquid from one jug into another.
P
In the previous post, <a href="http://blancosilva.github.io/post/2016/07/29/decanting.html">Decanting Problems and Dijkstra's Algorithm</a>, we presented some `scipy` hackery to solve the *Die Hard* puzzle:

> Two men have a full eight-gallon jug of wine, and also two empty jugs of five and three gallons capacity, respectively.  Is it possible (within the restrictions of our problem) to divide the wine equally so each men can have four gallons of wine?

In this post, we replicate the same technique, but this time using <a href="http://julialang.org/">Julia</a>'s `Graphs` package.  First of all, make sure you have the package installed.  If this is not the case, issue in an `Ijulia` session the command `Pkg.add("Graphs")`.  Once installed, the functions of the package can be readily called.  For an explanation of the different steps needed to solve this puzzle, make sure to read the previous post (linked above).

{% highlight julia %}
using Graphs

states = filter(x->x[1]+x[2]+x[3]==8 && 
				(x[1]==0 || x[1]==8 || x[2]==0 || x[2]==5 || x[3]==0 || x[3]==3) , 
       			[(a,b,c) for a in 0:8, b in 0:5, c in 0:3])
{% endhighlight %}

{% highlight text %}
16-element Array{Tuple{Int64,Int64,Int64},1}:
 (8,0,0)
 (7,1,0)
 (6,2,0)
 (5,3,0)
 (4,4,0)
 (3,5,0)
 (7,0,1)
 (2,5,1)
 (6,0,2)
 (1,5,2)
 (5,0,3)
 (4,1,3)
 (3,2,3)
 (2,3,3)
 (1,4,3)
 (0,5,3)
{% endhighlight %}

{% highlight julia %}
G = graph(states,[],is_directed=true)

for node1 in G.vertices
    for node2 in G.vertices
        total_change = ((node1[1]-node2[1]), node1[2]-node2[2], node1[3]-node2[3])
                 # Check 1: one of the jugs is not affected
        check1 = (total_change[1]*total_change[2]*total_change[3]==0)
                 # Check 2: one of the jugs gets full
        check2 = (node2[1]==8 && total_change[1]!=0) || 
        (node2[2]==5 && total_change[2]!=0) || 
        (node2[3]==3 && total_change[3]!=0)
                 # Check 3: one of the jugs gets empty
        check3 = (node2[1]==0 && total_change[1]!=0) || 
        (node2[2]==0 && total_change[2]!=0) || 
        (node2[3]==0 && total_change[3]!=0)
        is_adjacent = check1 && (check2 || check3)
        if is_adjacent 
            add_edge!(G, node1, node2)
        end
    end
end
{% endhighlight %}

We are ready to fire Dijkstra's algorithm on this graph now.  Note that, by construction, the state \\( (8,0,0) \\) is the 1st node, and the state \\( (4,4,0) \\) ---our goal--- is the 5th node.

{% highlight julia %}
r = dijkstra_shortest_paths(G, ones(Int64,num_edges(G)), (8,0,0))
{% endhighlight %}

{% highlight text %}
Graphs.DijkstraStates{Tuple{Int64,Int64,Int64},Int64,
DataStructures.MutableBinaryHeap{Graphs.DijkstraHEntry{Tuple{Int64,Int64,Int64},Int64},
DataStructures.LessThan},Int64}([(8,0,0),(7,0,1),(3,2,3),(5,0,3),(1,4,3),(8,0,0),(2,5,1),
(2,3,3),(6,2,0),(6,0,2),(8,0,0),(7,1,0),(3,5,0),(5,3,0),(1,5,2),(3,5,0)],[1,7,13,11,15,1,
8,14,3,9,1,2,6,4,10,6],[0,6,3,2,7,1,5,4,4,5,1,7,2,3,6,2],[2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2],
MutableBinaryHeap(),[0,12,7,5,15,1,10,8,9,11,2,14,3,6,13,4])
{% endhighlight %}

{% highlight julia %}
target = (8,0,0)
source = (4,4,0)
source_index=5

while source!=target
    print(source)
    new_index = r.parent_indices[source_index]
    source = r.parents[source_index]
    source_index = new_index
end
print(source)
{% endhighlight %}

{% highlight text %}
(4,4,0)(1,4,3)(1,5,2)(6,0,2)(6,2,0)(3,2,3)(3,5,0)(8,0,0)
{% endhighlight %}

As in the previous solution, we found that the simplest way to divide the wine equally is in 7 steps as follows:

1. Pour 5 gallons of wine into the second jug. \\( (3,5,0) \\)
2. Pour 3 gallons from the second jug to the third.  \\( (3,2,3) \\)
3. Pour 3 gallons from the third to the first. \\( (6,2,0) \\)
4. Pour all 2 gallons from the second to the third jug. \\( (6,0,2) \\)
5. Pour five gallons from the first to the second jug. \\( (1,5,2) \\)
6. Pour one gallon from the second to the third jug. \\( (1,4,3) \\)
7. We are technically done, but we may pour now all three gallons from the third jug to the first, for a convenient transportation of the wine. \\( (4,4,0) \\)

