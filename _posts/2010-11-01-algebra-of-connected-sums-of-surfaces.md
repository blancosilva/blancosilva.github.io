---
layout: page
title: Algebra of connected sums of surfaces
category: course-material
topic: topology
comments: true
---

Let us explore the algebraic properties of connected sums.  We immediately realize that the operation is both commutative

> <span>\\( S \mathop{\\#} S' = S' \mathop{\\#} S \\)</span> for any two surfaces <span>\\( S \\)<span> and <span>\\( S' \\)<span>,

and associative

> <span>\\( ( S \mathop{\\#} S') \mathop{\\#} S'' = S \mathop{\\#} (S' \mathop{\\#} S'') \\)<span> for any three surfaces <span>\\( S \\)<span>, <span>\\( S' \\)<span> and <span>\\( S'' \\)<span>.

The sphere acts a neutral element (like the zero for the addition of numbers):

> <span>\\( S \mathop{\\#} \mathbb{S}\_2 = S \\)<span> for all surfaces <span>\\( S \\)<span>.

Notice that, unlike addition of numbers, we do not necessarily have "negative surfaces": we cannot guarantee, for a given surface <span>\\( S \\)<span>, the existence of another surface <span>\\( S' \\)<span> such that <span>\\( S \mathop{\\#} S' = \mathbb{S}\_2 \\)<span>.

<a href="http://blancosilva.github.io/course-material/2010/10/29/surfaces.html">We have already seen</a> that the connected sum of two tori results in a two-genus torus.  In general, for any natural number <span>\\( n \in \mathbb{N}, \\)<span> the connected sum of <span>\\( n \\)<span> tori is a torus with genus <span>\\( n, \\)<span> wich we denote <span>\\( n \mathbb{T} = \mathbb{T} \mathop{\\#} \overset{n}{\dotsb} \mathop{\\#} \mathbb{T}. \\)<span>

The connected sum of two real projective spaces is a Klein bottle, <span>\\( \mathbb{K}. \\)<span>  To construct this connected sum from the representation of real projective planes as squares with sides identifies, note first what happens when we cut such a diagram into three stripes:

<table style="width:75%;border:4px solid black; margin-left:auto; margin-right:auto;">
<tbody>
<tr>
<td style="width:30%;text-align:center;vertical-align:middle;border-width:0;padding:10px;"><img src="http://farm5.static.flickr.com/4086/5138692210_2f2974cca8_o_d.jpg" alt="" width="100%" /></td>
<td style="width:70%;text-align:justify;vertical-align:top;padding:10px;" rowspan="2">Notice that the central stripe (in <span style="color:red;">red</span>) is a <a href="http://blancosilva.github.io/course-material/2010/11/02/mobius-bands-and-kleins-bottles.html" target="_self">Möbius band</a>.  Gluing the remaining two stripes through the common edge \( b \) properly, and identifying the other edges of these stripes accordingly, gives a disk.  We have thus proved that the removal of a (closed) disk from a projective space gives us a Möbius band.

We may consider this to be the disk that we remove prior to the gluing of the two real projective planes. Therefore, a connected sum of these two surfaces is equivalent to the union of two Möbius bands, with no need to perform any identification on edges a priori.

The statement is then proven, since we know that a given <a href="http://blancosilva.github.io/course-material/2010/11/02/mobius-bands-and-kleins-bottles.html" target="_self">Klein bottle can be split into a union of two Möbius bands</a>.</td>
</tr>
<tr>
<td style="width:30%;text-align:center;vertical-align:middle;border-width:0;padding:10px;"><img src="http://farm2.static.flickr.com/1233/5138692258_3e355a2e11_o_d.jpg" alt="" width="100%" /></td>
</tr>
</tbody>
</table>

<br />

The following property is very useful to understand topological simplification to the description of complicated connected sums:

> <span>\\( 3\mathbb{P} = \mathbb{T} \mathop{\\#} \mathbb{P} \\)<span>; that is, the connected sum of three real projective planes is homeomorphic to the connected sum of a torus with a real projective plane.

Or in other words, <span>\\( \mathbb{K} \mathop{\\#} \mathbb{P} = \mathbb{T} \mathop{\\#} \mathbb{P}. \\)<span> The proof of this result is a nice exercise, and I urge the reader to enjoy finding it by manipulation of the proper polygons.

We are at an excellent point to test our algebraic skills with the connected sum.  For example, consider the surface <span>\\( M \\)<span> constructed as the connected sum

<div>
\begin{equation}
 M = \mathbb{P} \mathop{\#} \mathbb{T} \mathop{\#} \mathbb{P} \mathop{\#} \mathbb{S}_2 \mathop{\#} \mathbb{P} \mathop{\#} \mathbb{K}.
 \end{equation}
</div>

The basic algebraic properties above allow us to give a simplified description of this surface:

<div>
\begin{align}
 M & = \mathbb{P}\mathop{\#}\mathbb{T}\mathop{\#}\mathbb{P}\mathop{\#}\mathbb{S}_2\mathop{\#}\mathbb{P}\mathop{\#}\mathbb{K} && \text{(group in pairs)}\\  
 & =  \big(\underbrace{\mathbb{P}\mathop{\#}\mathbb{T}}_{\mathbb{T}\mathop{\#}\mathbb{P}=3\mathbb{P}}\big)\mathop{\#}\big(\underbrace{\mathbb{P}\mathop{\#}\mathbb{S}_2}_{S\mathop{\#}\mathbb{S}_2=S}\big)\mathop{\#}\big(\mathbb{P}\mathop{\#}\underbrace{\mathbb{K}}_{2\mathbb{P}}\big) && \text{(simplify each pair)}\\  
 & = 3\mathbb{P}\mathop{\#}\mathbb{P}\mathop{\#}3\mathbb{P}=7\mathbb{P} 
 \end{align}
</div>
