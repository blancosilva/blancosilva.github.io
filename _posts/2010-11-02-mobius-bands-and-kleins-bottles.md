---
layout: page
title: Möbius bands and Klein bottles
date: 2010-11-02 00:59:51.000000000 -04:00
category: course-material
topic: topology
comments: true
---

Consider a long and narrow strip of paper, in which we glue the two narrower edges together after performing a half-twist of the strip, hence forming a funny-looking loop.  Topologically, this is equivalent to identifying two parallel edges of a square in the proper way.  Therefore, we can see the Möbius band as the quotient space of <span>\\( \square_2 \\)</span> with the following equivalence relation: Given <span>\\( (x_1,x_2), (y_1,y_2) \in \square_2, \\)</span> we write <span>\\( (x_1,x_2) \sim (y_1,y_2) \\)</span> if

1. <span>\\( x_1=y_1 \\)</span> and <span>\\( x_2=y_2, \\)</span> or
2. <span>\\( x_2 y_2 = -1 \\)</span> and <span>\\( x_1 = 1-y_1. \\)</span>

<table style="width:50%;margin-left:auto;margin-right:auto;border-width:0;">
<tbody>
<tr>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:0;"><img src="http://farm5.static.flickr.com/4061/5138306803_a74b9b45e1_o_d.jpg" alt="" width="100%" /></td>
<td style="text-align:center;vertical-align:middle;width:50%;border-width:0;"><img src="http://farm5.static.flickr.com/4112/5138306843_614839a353_o_d.jpg" alt="" width="100%" /></td>
</tr>
</tbody>
</table>

In a similar fashion, we construct a new surface by identification of two parallel edges of a square to form a cylinder, and a posterior identification of the remaining two edges (which turned into two circles after the first identification).  The second identification will be performed after a "half-twist" (which unfortunately can only be realized in a fourth dimension!).  The equivalence relation in the square <span>\\( \square_2 \\)</span> is as follows: Given <span>\\( (x_1,x_2), (y_1,y_2) \in \square_2, \\)</span> we define <span>\\( (x_1,x_2) \sim (y_1,y_2) \\)</span> provided one of the following conditions are satisfied:

1. <span>\\( x_1=y_1 \\)</span> and <span>\\( x_2=y_2, \\)</span> or
2. <span>\\( x_1 y_1 = -1 \\)</span> and <span>\\( x_2 = y_2 \\)</span>, or
3. <span>\\( x_2 y_2 = -1 \\)</span> and <span>\\( x_1 = 1-y_1. \\)</span>

A diagram representing this quotient space—which we denote <span>\\( \mathbb{K} \\)</span> and call Klein bottle—is shown below, together with an interesting way to split and recover the space:  Notice how by cutting three stripes in the manner shown, and adjoining two of the stripes through the proper edge, we can see the Klein's bottle as the union of two Möbius bands.

<p style="text-align:center;"><img src="http://farm2.static.flickr.com/1210/5139208635_bde30eca52_b_d.jpg" alt="" width="75%" /></p>

## Miscellaneous

All the images included in this presentation are generated with the aid of the package `tikz` in <span>\\( \LaTeX \\)</span>.  The code that created the Möbius strip above, for example, is given by

{% highlight latex linenos %}
\documentclass{amsart}
\usepackage{tikz}
\usetikzlibrary{calc}
\begin{document}
\begin{tikzpicture}
\coordinate (a) at (0cm,0cm);
\coordinate (b) at (1cm,0cm);
\coordinate (c) at (60:1cm);
\coordinate (ab1) at ($ (a)!.25!(b) $);
\coordinate (ab2) at ($ (a)!.75!(b) $);
\coordinate (bc1) at ($ (b)!.25!(c) $);
\coordinate (bc2) at ($ (b)!.75!(c) $);
\coordinate (ac1) at ($ (a)!.25!(c) $);
\coordinate (ac2) at ($ (a)!.75!(c) $);
\draw[fill=red!60!black,thick,rounded corners=2pt] (ab1) -- (bc2) [rounded corners=1pt] --(ac2) -- (ac1) [rounded corners=2pt] --cycle;
\draw[fill=red!80!black,thick] (bc1) [rounded corners=2pt] --(bc2) [rounded corners=1pt]-- (ac2) [rounded corners=2pt]-- (ab2) [rounded corners=1pt] --cycle;
\draw[fill=red,thick] (ab1) [rounded corners=2pt] -- (ab2) [rounded corners=1pt] -- (bc1) -- (ac1) [rounded corners=2pt] -- cycle;
\end{tikzpicture}
\end{document}
{% endhighlight %}
