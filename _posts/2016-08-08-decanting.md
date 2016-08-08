---
title: Decanting Problems and Dijkstra's Algorithm (II)
date: 2016-08-08 02:52:00
layout: post
category: post
comments: true
image:
  teaser: http://blancosilva.github.io/images/amphora.jpg
---

In the previous post, <a href="http://blancosilva.github.io/post/2016/07/29/decanting.html">Decanting Problems and Dijkstra's Algorithm</a>, we presented some `scipy` hackery to solve the *Die Hard* puzzle:

> Two men have a full eight-gallon jug of wine, and also two empty jugs of five and three gallons capacity, respectively.  Is it possible (within the restrictions of our problem) to divide the wine equally so each men can have four gallons of wine?

In this post we replicate the same technique, but this time using <a href="http://julialang.org/">Julia</a>'s `Graphs` package.  First of all, make sure you have the package installed.  If this is not the case, issue in an `Ijulia` session the command `Pkg.add("Graphs")`.  Once installed, the functions of the package can be readily called.  

<div class="alert alert-warning" role="alert" style="text-align:center;">
	For an explanation of the different steps needed to solve this puzzle, make sure to read the previous post (linked above).  Also, we have omitted most irrelevant outputs for a simpler exposition.
</div>

{% highlight julia linenos %}
using Graphs

states = filter(x->x[1]+x[2]+x[3]==8 && 
                (x[1]==0 || x[1]==8 || x[2]==0 || x[2]==5 || x[3]==0 || x[3]==3) , 
                [(a,b,c) for a in 0:8, b in 0:5, c in 0:3])

G = graph(states, [], is_directed=true)

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

{% highlight julia linenos %}
r = dijkstra_shortest_paths(G, ones(Int64,num_edges(G)), (8,0,0))

target = (8,0,0)
source = (4,4,0)
source_index = 5

while source!=target
    print(source)
    source = r.parents[source_index]
    source_index = r.parent_indices[source_index]
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

