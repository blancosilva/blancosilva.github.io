---
layout: post
title: El País' weekly challenge
date: 2011-04-12 08:55:51.000000000 -04:00
category: post
image:
  teaser: https://i0.wp.com/farm6.static.flickr.com/5302/5612612083_f60c635409.jpg
---

For a while now, the Spanish newspaper "El País" has been posing a weekly mathematical challenge to promote a collection of books, and celebrate a hundred years of their country's Royal Mathematical Society.

The latest of these challenges—the fourth—is a beautiful problem in combinatorics:

<div class="well">
	Consider a clock, with its twelve numbers around a circle: \( 1, 2, \dotsc, 12.\)  Color each of the twelve numbers in either blue or red, in such a way that there are exactly six in red, and six in blue.  Proof that, independently of the order chosen to color the numbers, there always exists a line that divides the circle in two perfect halves, and on each half there will be exactly three numbers in red, and three numbers in blue.
</div>

While there are many different ways to solve this challenge, I would like to propose here one that is solely based upon purely counting techniques.

The first step is "coding" the clock: To every situation, we assign a new clock where each number has been substituted with plus and minus ones: <span>\\( +1 \\)</span> instead of a <font color="blue">blue number</font>, and a <span>\\( -1 \\)</span> instead of any <font color="red">red number</font>.

<p style="text-align:center;"><a href="http://www.flickr.com/photos/eseprimo/5612612083/" title="relojes by eseprimo, on Flickr"><img src="https://i0.wp.com/farm6.static.flickr.com/5302/5612612083_f60c635409.jpg" alt="relojes" /></a></p>

Notice that, if you add all the plus and minus ones in the second clock, you obtain zero: this is of course, due to the fact that there are as many blue as red numbers.

Consider any line that divides the circle in two equal halves: let <span>\\( M \\)</span> be the sum of plus and minus ones of one of the halves.  The previous property tells us that the sum of plus and minus ones of the other half must be precisely <span>\\( -M \\)</span>.

<div class="well">
	For example, in the clock above, consider the two halves containing the hours 1 through 6, and 7 through 12.  The sum of plus and minus ones for the former is \( -1-1+1-1+1-1=-4+2=-2, \) and hence it will be \( +2 \) for the latter.

	Note that, no matter the half chosen, the sums \( M \) of plus and minus ones for this particular example are always going to be even numbers.
</div>

To solve our problem, all we have to do is **prove** that there exists a line that divides the clock in such a way that the sums of plus and minus ones of both halves is precisely zero.  How are we going to prove it?

Assume we choose a given half, and the value of the sum of its plus and minus ones is not zero.  Now, rotate that line one hour clockwise.  The sum of ones and minus ones of the new halves change, but the way they change is by not too much.  If the sum of ones and minus ones of the previous half was <span>\\( M \\)</span>, then the sum of ones and minus ones of the new half can only be:

* <span>\\( M+2 \\)</span> in case we lose a red <span>\\( (-1) \\)</span> and gain a blue <span>\\( (+1) \\)</span>
* <span>\\( M \\)</span> in case we lose and gain the same color.
* <span>\\( M-2 \\)</span> in case we lose a blue <span>\\( (+1) \\)</span> and gain a red <span>\\( (-1) \\)</span>

Another important fact derived of this property is that, no matter how we half the clock, the parity of the sum of plus and minus ones for each half is always the same (that is, they are all even, or they are all odd).

Notice what happened: We started picking a half of the clock.  The sum of plus and minus ones for that half was some value <span>\\( M \\)</span>.  If this value is zero, then we are done.  But if not, by rotating the line clockwise six times, we go from <span>\\( M \\)</span> to <span>\\( -M \\)</span> by adding or subtracting <span>\\( 2 \\)</span> (or keeping the same value).  We **have** to cross the zero at some point!

And this is the punch-line: all we need to prove now is that, no matter the arrangement of colors for the numbers in any clock, and no matter how we half them, the sum of the corresponding plus and minus ones of each half is **always** even.   This guarantees us that, when we cross zero, we do it so by actually finding a line with the required properties.  How would you prove this fact?

<p style="text-align:center;"><a href="http://www.flickr.com/photos/eseprimo/5613328410/" title="masrelojes by eseprimo, on Flickr"><img src="https://i0.wp.com/farm6.static.flickr.com/5145/5613328410_2dcbb61737_o.jpg" width="60%" alt="masrelojes" /></a></p>

I encourage you to also find other ways to solve this challenge.  Feel free to use big theorems from Combinatorics, code the clock as a graph and use techniques of that field… anything goes.
