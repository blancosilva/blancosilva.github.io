---
layout: post
title: What is the next number?
date: 2010-10-15 14:37:54.000000000 -04:00
category: post
comments: true
image:
  teaser: https://i0.wp.com/farm5.static.flickr.com/4132/5084588268_0a448b9d35_o_d.jpg
---
A classical problems with sequences:

<div class="well">
	What is the next term in the following sequence?

	\begin{equation}
	\frac{8}{3}, \frac{87}{32}, \frac{878}{323}, \frac{2721}{1001} 
	\end{equation}
</div>

I particularly enjoy this kind of problem where a sequence of numbers <span>\\( \big\\{ x_1, x_2, x_3, x_4, \dotsc \big\\} \\)</span> is given, and you have to find the next one, or the general term <span>\\( x_n \\)</span>. Some easy examples follow:

<div>
	\begin{gather}
	\big\{ 1, 1, 1, 1, 1, 1, \dotsc \big\} \\
	\big\{1, 2, 3, 4, 5, 6, \dotsc\big\} \\
	\big\{1, 2, 4, 8, 16, 32, \dotsc\big\} \\
	\big\{1, 1, 2, 3, 5, 8, \dotsc\big\} 
	\end{gather}
</div>

The last example of that series is the famous Fibonacci sequence: every number is the sum of the previous two.  The general term of this sequence has therefore the expression <span>\\( x\_n = x\_{n-1} + x\_{n-2}. \\)</span>

Every now and then, one finds a particularly tough sequence, for which there is no apparent logic behind the choice of next term.  Fortunately, there are databases of sequences online that help you find your way.  Google or WolframAlpha are very useful in this sense.  I have included below the results of searching for a few terms of the Fibonacci sequence in both.

The sequence of fractions at the beginning of the post is indeed a difficult one.  What can we say about these numbers, that would help us find the general term?  For instance, the floating point value of each number is <span>\\( \big\\{ 2.\overline{6}, 2.71875, 2.71827, 2.71828 \big\\} \\)</span>.  These are all very close to the value of the Euler number:

<div>
	\begin{equation}
	e \approx 2.7182818284590452353602874713526624977572470936999595749669 \dotsc</td>
	\end{equation}
</div>

Another clue: the first fraction has a single digit both in the numerator and the denominator.  The second fraction has two digits, the third fraction three, and the fourth fraction, well, four.

Something not so easy to realize is that the first number is actually, among all fractions with a single digit both in numerator and denominator, **the one that approximates best to the Euler number**.  The same property is shared by the other elements of the sequence:  For example, the third number is among the fractions with three digits both in numerator and denominator, the one that best approximates to the Euler number.

I have given you enough information; the question that remains now is:

> Among the fractions with five digits on the numerator and five digits in the denominator, which one offers the best approximation to the Euler number?

And the natural follow-up question:

> Is there a general method to calculate such fractions, other than looking at all the possibilities?

### Miscellaneous

<div class="row">
	<div class="col-lg-6">
		<img src="https://i0.wp.com/farm5.static.flickr.com/4087/5084588104_66fc701a9f_o_d.jpg" alt="" width="100%" />
	</div>
	<div class="col-lg-6">
		<img src="https://i0.wp.com/farm5.static.flickr.com/4132/5084588268_0a448b9d35_o_d.jpg" alt="" width="100%" />
	</div>
</div>
