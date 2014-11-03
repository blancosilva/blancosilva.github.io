---
layout: post
title: Areas of Mathematics
date: 2013-10-22 16:48:37.000000000 -04:00
category: post
image:
  teaser: "https://i0.wp.com/farm8.staticflickr.com/7451/10428227193_109ee4dd96_o_d.jpg"
---

For one of my upcoming talks I am trying to include an exhaustive mindmap showing the different areas of Mathematics, and somehow, how they relate to each other.  Most of the information I am using has been processed from years of exposure in the field, and a bit of help from Wikipedia.

<p><img src="https://i0.wp.com/farm8.staticflickr.com/7451/10428227193_109ee4dd96_o_d.jpg" style="width:100%;text-align:center;margin-left:auto;margin-right:auto;" />

But I am not entirely happy with what I see:  my lack of training in the area of Combinatorics results in a rather dry treatment of that part of the mindmap, for example.  I am afraid that the same could be told about other parts of the diagram.  Any help from the reader to clarify and polish this information will be very much appreciated.

And as a bonus, I included a \(\LaTeX\) script to generate the diagram with the aid of the `tikz` libraries.

{% highlight tex linenos %}
\tikzstyle{level 2 concept}+=[sibling angle=40]
\begin{tikzpicture}[scale=0.49, transform shape]
  \path[mindmap,concept color=black,text=white]
    node[concept] {Pure Mathematics} [clockwise from=45]
      child[concept color=DeepSkyBlue4]{
        node[concept] {Analysis} [clockwise from=180]
          child {
            node[concept] {Multivariate \& Vector Calculus}
              [clockwise from=120]
              child {node[concept] {ODEs}}}
              child { node[concept] {Functional Analysis}}
              child { node[concept] {Measure Theory}}
              child { node[concept] {Calculus of Variations}}
              child { node[concept] {Harmonic Analysis}}
              child { node[concept] {Complex Analysis}}
              child { node[concept] {Stochastic Analysis}}
              child { node[concept] {Geometric Analysis}
                [clockwise from=-40]
                child {node[concept] {PDEs}}}}
          child[concept color=black!50!green, grow=-40]{
            node[concept] {Combinatorics} [clockwise from=10]
              child {node[concept] {Enumerative}}
              child {node[concept] {Extremal}}
              child {node[concept] {Graph Theory}}}
          child[concept color=black!25!red, grow=-90]{
            node[concept] {Geometry} [clockwise from=-30]
              child {node[concept] {Convex Geometry}}
              child {node[concept] {Differential Geometry}}
              child {node[concept] {Manifolds}}
              child {node[concept,color=black!50!green!50!red,text=white] {Discrete Geometry}}
              child {
                node[concept] {Topology} [clockwise from=-150]
                  child {node [concept,color=black!25!red!50!brown,text=white]
                    {Algebraic Topology}}}}
          child[concept color=brown,grow=140]{
            node[concept] {Algebra} [counterclockwise from=70]
              child {node[concept] {Elementary}}
              child {node[concept] {Number Theory}}
              child {node[concept] {Abstract} [clockwise from=180]
                child {node[concept,color=red!25!brown,text=white] {Algebraic Geometry}}}
              child {node[concept] {Linear}}}
    node[extra concept,concept color=black] at (200:5) {Applied Mathematics}
      child[grow=145,concept color=black!50!yellow] {
        node[concept] {Probability} [clockwise from=180]
          child {node[concept] {Stochastic Processes}}}
      child[grow=175,concept color=black!50!yellow] {node[concept] {Statistics}}
      child[grow=205,concept color=black!50!yellow] {node[concept] {Numerical Analysis}}
      child[grow=235,concept color=black!50!yellow] {node[concept] {Symbolic Computation}};
\end{tikzpicture}
{% endhighlight %}
