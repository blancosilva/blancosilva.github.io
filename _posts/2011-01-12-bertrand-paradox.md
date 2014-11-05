---
layout: post
title: Bertrand Paradox
date: 2011-01-12 13:37:20.000000000 -05:00
category: post
comments: true
image:
  teaser: "https://farm8.staticflickr.com/7526/15528806130_1944b2d5df_n_d.jpg"
---

Classically, we define the probability of an event as the ratio of the favorable cases, over the number of all possible cases.  Of course, these possible cases need to be all equally likely.  This works great for discrete settings, like dice rolls, card games, etc.  But when facing non-discrete cases, this definition needs to be revised, as the following example shows:

> Consider an equilateral triangle inscribed in a circle. Suppose a chord of the circle is chosen at random. What is the probability that the chord is longer than a side of the triangle?

<table style="background-color:#F4F5F7;width:100%;border-width:0;">
<tr>
<td style="text-align:center;width:33%;border-width:0;"><a href="http://blancosilva.files.wordpress.com/2011/01/161px-bertrand1-figure-svg.png"><img src="assets/161px-bertrand1-figure-svg.png" alt="" title="161px-Bertrand1-figure.svg" width="100%" /></a>
</td>
<td style="text-align:center;width:33%;border-width:0;"><a href="http://blancosilva.files.wordpress.com/2011/01/161px-bertrand2-figure-svg.png"><img src="assets/161px-bertrand2-figure-svg.png" alt="" title="161px-Bertrand2-figure.svg" width="100%" /></a>
</td>
<td style="text-align:center;width:33%;border-width:0;"><a href="http://blancosilva.files.wordpress.com/2011/01/161px-bertrand3-figure-svg.png"><img src="assets/161px-bertrand3-figure-svg.png" alt="" title="161px-Bertrand3-figure.svg" width="100%" /></a>
</td>
</tr>
<tr>
<td style="text-align:center;border-width:0;">First example</td>
<td style="text-align:center;border-width:0;">Second example</td>
<td style="text-align:center;border-width:0;">Third example</td>
</tr>
</table>

Using the classical definition of probability, three different students attacked this problem independently, and found each a different result:  In all three examples, assume the circle has radius 1.

* Fix any point, say <span>\\( P \\)</span> in the circle.  Consider any random chord in the circle, by choosing any other point <span>\\( Q \\)</span> on it.  The number of possible cases is thus <span>\\( (2\pi \times 1)^2 = 4\pi^2. \\)</span>  Place one of the vertices of the equilateral triangle on <span>\\( P \\)</span>, and notice that the circle gets partitioned in three arcs with equal length <span>\\( (\tfrac{2\pi}{3}). \\)</span>  Only if <span>\\( Q \\)</span> belongs in the arc farthest to <span>\\( P, \\)</span> we will have a chord longer than the side of the triangle.  Therefore, the number of favorable cases is <span>\\( 2\pi \times \tfrac{2\pi}{3} = \tfrac{4\pi^2}{3}. \\)</span> Consequently, the probability we are looking for is <span>\\( \tfrac{1}{3}. \\)</span></li>
* Choose any point <span>\\( P \\)</span> on the circle, any point <span>\\( Q_P \\)</span> on the radius <span>\\( r_P=\overline{0P}, \\)</span> and consider the chord formed from the perpendicular to <span>\\( r_P \\)</span> by <span>\\( Q_P. \\)</span>  There are <span>\\( 2\pi \times 1 = 2\pi \\)</span> possible cases.  Place the equilateral triangle so that one of the sides is perpendicular to <span>\\( r_P, \\)</span> and notice that the number of favorable cases coincide with those chords where <span>\\( Q_P \\)</span> is nearer the center of the circle than the point where the side of the triangle intersects the radius.  A simple trigonometric computation tells us that the number of favorable cases is precisely <span>\\( 2\pi \times \tfrac{1}{2} = \pi, \\)</span> and thus the probability we are looking for is <span>\\( \tfrac{1}{2}. \\)</span></li>
* Choose any point <span>\\( P \\)</span> in the interior of the disk, and consider the only chord that has <span>\\( P \\)</span> as a midpoint.  There are <span>\\( \pi \times 1^2 = \pi \\)</span> possible cases.  The chord will be longer than the side of the triangle, only if the chosen point falls within a concentric circle of radius <span>\\( \tfrac{1}{2}. \\)</span>  The number of favorable cases is thus the area of this circle: <span>\\( \pi \times \big( \tfrac{1}{2} \big)^2 = \tfrac{\pi}{4}. \\)</span>  The probability we are looking for is in this case <span>\\( \tfrac{1}{4}. \\)</span></li>

The three methods are sound: why did we get different answers?  Which student do you think got it "right"?  Can you explain what the paradox is in this situation?
