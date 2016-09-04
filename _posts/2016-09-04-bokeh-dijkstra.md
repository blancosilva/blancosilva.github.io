---
layout: post
title: Interactive Shortest-distance calculations on Triangulations
date: 2016-09-04 
category: post
current: true
comments: true
image:
  teaser: http://blancosilva.github.io/images/bokeh-dijkstra.jpg
---

As a means to bring attention to my latest book, <a href="https://www.amazon.com/gp/product/1783984740/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1783984740&linkCode=as2&tag=blancosilva-20&linkId=c8c86543cb20b2f40701f081b1d5ffcd">Mastering SciPy</a>, I wrote a blog post summarizing some of the techniques illustrated in one of its chapters: <a href="http://blancosilva.github.io/post/2014/10/28/Computational-Geometry-in-Python.html">Computational Geometry in Python</a>.  On that post, I created an example of computation of shortest distances between two vertices of the constrained conforming Delaunay triangulation of a polygon with holes, in which I imposed a maximum allowed area on the required triangles.  To illustrate this technique, I chose two vertices randomly, produced the code to calculate the sequence of segments that facilitate the shortest path between them, and presented the corresponding visualization.

Ever since publishing that post, I thought it would be even nicer to have an interactive diagram, where just by hovering over the vertices of the triangulation, we could quickly compute and display those paths.  It took me a while, but now with the assistance of `bokeh`, it came to fruition.  Well, here it is!

Use the mouse wheel to zoom in and out, drag and drop to pan the underlying triangulation, and notice what happens when the mouse hovers over each of the vertices.

<link rel="stylesheet" href="https://cdn.pydata.org/bokeh/release/bokeh-0.12.1.min.css" type="text/css" />
        
<script type="text/javascript" src="https://cdn.pydata.org/bokeh/release/bokeh-0.12.1.min.js"></script>
<script type="text/javascript"> Bokeh.set_log_level("info"); </script>

<script type="text/javascript">
Bokeh.$(function() {
    var render_items = [{"docid":"aa35f7bf-4f5d-4241-9411-a61760ef0c63","elementid":"9f7fea17-8e58-46cb-a7f0-111dfbbb4042","modelid":"722807a2-0810-44d0-8653-25cfbfa51ccd"}];
    
    Bokeh.embed.embed_items(docs_json, render_items);
});
</script>



<script type="text/javascript">
    Bokeh.$(function() {
    var render_items = [{"docid":"d5b6724e-e0da-4b7c-ab43-7fa2b6311e2e","elementid":"546ccb53-63a6-4c56-bc6e-4ecb310e397d","modelid":"0c2d72ce-52ee-432c-9d42-4d5c6e8eb8fb"}];
    
    Bokeh.embed.embed_items(docs_json, render_items);
});
</script>

<div class="bk-root">
    <div class="plotdiv" id="546ccb53-63a6-4c56-bc6e-4ecb310e397d"></div>
</div>