---
layout: post
title: Exact Expression
date: 2010-11-15 00:02:52.000000000 -05:00
category: post
comments: true
---

<div class="well">
	Find the exact expression for the infinite sum
	\begin{equation}
	\frac{1}{1} + \frac{2}{2+3} + \frac{3}{4+5+6} + \frac{4}{7+8+9+10} + \dotsb
	\end{equation}
</div>

### Solution

The usual method starts by rewriting the infinite sum in a compact form, <span>\\( \sum_{n=1}^\infty f(n), \\)</span> for an appropriate function <span>\\( f. \\)</span>  We do so after the following observations:

* The <span>\\( n \\)</span>-th term of the sum is a fraction, for which the numerator coincides with the number <span>\\( n. \\)</span>
* We can see the denominator of the <span>\\( n \\)</span>-th term as the difference of two sums.  Notice that the largest term of those sums coincides with the sum of all the positive integers from one to <span>\\( n. \\)</span>  The smallest term in the sums of the denominators is one unit larger than the sum of all positive integers from one to <span>\\( n-1. \\)</span>   Analytically, this is the following expression:
    <div>
    	\begin{equation}
    	\underbrace{\dfrac{1}{2}\,\overbrace{\dfrac{n(n+1)}{2}}^{1+\dotsb+n}\bigg(\dfrac{n(n+1)}{2}+1\bigg)}_{1+\dotsb+\tfrac{n(n+1)}{2}}-\underbrace{\dfrac{1}{2}\,\overbrace{\dfrac{n(n-1)}{2}}^{1+\dotsb+(n-1)}\bigg(\dfrac{n(n-1)}{2}+1\bigg)}_{1+\dotsb+\frac{n(n-1)}{2}}
    	\end{equation}
    </div>
which reduces to <span>\\( \frac{1}{2}(n^3+n). \\)</span>

The last step is then to produce the sum of the expression

<div>
	\begin{equation}
	\sum_{n=1}^\infty \frac{2n}{n^3+n} = \sum_{n=1}^\infty \frac{2}{n^2+1}.
	\end{equation}
</div>

The *easy* way is to obtain the aid of a mathematical software package (`mathematica`, `maple`, `matlab`, ...)

For example, <a href="http://www.wolframalpha.com/input/?i=sum[2/(x^2%2B1),{x,1,infinity}]">www.wolframalpha.com/input/?i=sum[2/(x^2%2B1),{x,1,infinity}]</a> gives not only the answer (<span>\\( \pi \coth \pi -1 \\)</span>), but also important information about the sum: *Both the ratio and root tests are inconclusive, but the integral test indicates that the sum converges*.

How would the reader use this information to obtain the value of the sum by traditional methods?  The integral test only offers a crude estimation for the sum:  Since we know that

<div>
	\begin{equation}
	\int_1^\infty \frac{2}{x^2+1}\, dx \leq \sum_{n=1}^\infty \frac{2}{n^2+1} \leq 1 +\int_1^\infty \frac{2}{x^2+1}\, dx,
	\end{equation}
</div>

and in our case, as <span>\\( \int_1^\infty 2/(x^2+1)\, dx =\frac{\pi}{2} \\)</span>, we have the estimate

<div>
	\begin{equation}
	\frac{\pi}{2} \leq \sum_{n=1}^\infty \frac{2}{n^2+1} \leq 1+\frac{\pi}{2}.
	\end{equation}
</div>

We can go so much further with the Laplace transform: Notice first that the Laplace transform of <span>\\( \sin \omega t \\)</span> is precisely the expression <span>\\( \omega (s^2+\omega^2)^{-1}. \\)</span>  In this case, we may use this fact to rewrite the infinite sum as follows:

<div>
	\begin{equation}
	\sum_{n=1}^\infty \frac{2}{n^2+1} = 2 \sum_{n=1}^\infty \frac{1}{n^2+1} = 2 \sum_{n=1}^\infty \int_{0}^\infty e^{-nx} \sin x\, dx
	\end{equation}
</div>

Since we have proved that the series converges, we are allowed to change integral with summation. We obtain

<div>
	\begin{equation}
	\sum_{n=1}^\infty \frac{2}{n^2+1} = 2 \int_0^\infty \sin x \sum_{n=1}^\infty e^{-nx}\, dx = 2\int_0^\infty \frac{e^{-x}}{1-e^{-x}}\,\sin x \, dx
	\end{equation}
</div>

The key is therefore to find the last integral in the expression above.
