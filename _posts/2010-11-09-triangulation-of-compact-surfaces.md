---
layout: page
title: Triangulation of compact surfaces
category: course-material
topic: topology
comments: true
---

A triangulation of a compact surface <span>\\( S \\)</span> is a finite family of closed subsets <span>\\( \{ T_1, T_2, \dotsc, T_m\} \\)</span> that cover <span>\\( S, \\)</span> and a family of homeomorphisms <span>\\( \varphi_k: \mathcal{T} \to T_k \\)</span>, where <span>\\( \mathcal{T} \subset \mathbb{R}^2 \\)</span> is a proper triangle in the plane.  We say that the sets <span>\\( T_k \\)</span> are triangles as well, and the images by <span>\\( \varphi_k \\)</span> of a vertex (resp. edge) of the triangle <span>\\( \mathcal{T} \\)</span> is also called a vertex (resp. edge).  We impose one condition: Given two different triangles <span>\\( T_k \\)</span> and <span>\\( T_j, \\)</span> their intersection must be either void, or a common vertex, or a common edge.

<blockquote>
Since the (surface of a) tetrahedron is homeomorphic to the sphere \( \mathbb{S}_2, \) we may consider this as a valid triangulation for the latter.  This triangulation is formed basically by four triangles, four vertices and six edges.

<table style="width:75%; margin-left:auto; margin-right:auto;">
<tr>
<td style="text-align:center;vertical-align:middle;width:50%;"><img src="http://farm5.static.flickr.com/4001/5163063660_2c03604d19_o_d.jpg" width="100%" /></td>
<td style="text-align:center;vertical-align:middle;width:50%;"><img src="http://farm5.static.flickr.com/4147/5162456723_b2980d9744_o_d.jpg" width="100%" /></td>
</tr>
</table>

The following example shows a triangulation of a torus, performed on the representation of \( \mathbb{T} \) given by the quotient space of the square \( \square_2 \) by the proper identification in the border.  Note that in this representation, all of the vertices of the square are actually the same vertex, which we denote \( P_1. \)  We construct a triangulation by placing two more vertices on the horizontal borders, \( P_2, P_3, \) two more vertices in the vertical borders, \( P_4, P_5, \), four more vertices inside the square, \( P_6, P_7, P_8, P_9, \), and joining all of them with edges, as shown in the image below:
<table style="width:75%; margin-left:auto; margin-right:auto;">
<tr>
<td style="text-align:center;vertical-align:top;width:40%;border-width:0;">
<img src="http://farm5.static.flickr.com/4086/5161919213_ebf564f5f7_o_d.jpg" width="100%" /></td>
<td style="text-align:center;vertical-align:middle;width:60%;border-width:0;">
<img src="http://farm2.static.flickr.com/1202/5165763462_91305e8e7e_o_d.jpg" width="100%" /></td>
</tr>
</table>

This gives the following triangles:

<div>
\begin{equation} \begin{array}{ccc}P_1P_2P_5 & P_2P_5P_6 & P_2P_3P_6\\P_3P_6P_7 & P_1P_3P_6 & P_1P_5P_7\\P_4P_5P_6 & P_4P_6P_8 & P_6P_7P_8\\P_7P_8P_9 & P_4P_7P_9 & P_4P_5P_7\\P_1P_2P_4 & P_2P_4P_8 & P_2P_3P_8\\P_3P_8P_9 & P_3P_4P_9 & P_1P_3P_4\end{array} 
\end{equation}
</div>
</blockquote>

Two important observations about triangulations of **any** compact surface:

* Each edge belongs to exactly two triangles.  This is due to the fact that the surfaces have at every point, a neighborhood that is homeomorphic to an open ball.
* Given a vertex <span>\\( v \\)</span> in a proper triangulation, it is possible to sort all the triangles that share than vertex, say clock or counterclockwise, in such a way that two consecutive triangles share a common edge. This is a direct consequence of the previous observation, and the fact that the union of all the triangles sharing a common vertex must be a connected set.
