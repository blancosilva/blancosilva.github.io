---
layout: post
title: Probability and Divisibility by 11
date: 2010-10-20 09:30:01.000000000 -04:00
category: post
comments: true
---
<div class="well">
Seven different playing cards, with values from <em>ace</em> to <em>seven</em>, are shaken in a hat, then taken out singly and then placed in a row.  What is the probability that this seven-digit number is divisible by 11?
</div>

The probability above is computed by the usual quotient

<div>
	\begin{equation}
	P = \frac{\text{favorable cases}}{\text{possible cases}},
	\end{equation}
</div>

where there are <span>\\( 7! = 7 \cdot 6 \cdot 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 5040 \\)</span> possible numbers of seven digits with each of the digits different to each other, and member of the set <span>\\( \{ 1, 2, 3, 4, 5, 6, 7\} \\)</span>.  The number of favorable cases is given by how many of the possible cases are actually divisible by 11.  Finding those favorable cases by hand is an extremely tedious task, of course.  Can we find a more elegant—and faster—way to compute the number of favorable cases?  The trick is based on using the right test of divisibility by 11.

An example of test of divisibility by 11 goes like this: **Take the digits in a right-to-left  order, alternatively subtracting and adding.  Only if the final result is divisible by 11 will the original number be divisible by 11.**

For example, for the 7-digit number <span>\\( 1354267 \\)</span>, the divisibility test gives <span>\\( 7 - 6 + 2 - 4 + 5 - 3 + 1 = 2 \\)</span>, which is not divisible by 11 (therefore, neither is <span>\\( 135426 \\)</span>).

A few useful facts:

* Let us represent our particular seven-digit numbers by <span>\\( ABCDEFG \\)</span>, where each letter goes for a different digit of the set <span>\\( \{ 1, 2, 3, 4, 5, 6, 7\} \\)</span>.
* The test of divisibility by 11 on the previous number calls for the computation of
    <div>
    	\begin{equation}
    	G - F + E - D + C - B + A = (A + C + E + G) - (B + D + F).
    	\end{equation}
    </div>
* Notice that <span>\\( 1 + 2 + 3 + 4 + 5 + 6 + 7 = 28 \\)</span>, an even number.
* Remember the rules of addition of even and odd numbers:
    <div>
    	\begin{equation}
    	\begin{array}{rl} even + even &amp;= even \\ odd + odd &amp;= even \\ even + odd &amp;= odd \end{array}
    	\end{equation}
    </div>
* The latter two facts above imply that <span>\\( A + C + E + G \\)</span> and <span>\\( B + D + F \\)</span> both have the same parity (they are either both even or both odd at the same time).
* As a consequence of the last fact, the subtraction <span>\\( (A + C + E + G) - (B + D + F) \\)</span> has to be an even number too!
* The largest possible value for the test of divisibility by 11 in our numbers, <span>\\( (A + C + E + G) - (B + D + F) \\)</span>, happens for numbers where <span>\\( A \\)</span>, <span>\\( C \\)</span>, <span>\\( E \\)</span> and <span>\\( G \\)</span> are largest; that is, they are the permutations of the four digits <span>\\( \{ 4, 5, 6, 7 \} \\)</span>. This value is, of course, <span>\\( (7 + 6 + 5 + 4) -( 1+ 2 +3) = 22 -6 =16. \\)</span>
* The smallest possible value for the test of divisibility by 11 in our numbers happens for numbers where <span>\\( B \\)</span>, <span>\\( D \\)</span> and <span>\\( F \\)</span> are largest; that is, they are permutations of the three digits <span>\\( \{ 5, 6, 7\} \\)</span>.  This value is, of course, <span>\\( (1 + 2 + 3 + 4) - (5 + 6 + 7) = 10-18 = -8 \\)</span>.
* In our case, there are then only thirteen different possible tests of divisibility by 11: <span>\\( \{ -8, -6, -4, -2, 0 , 2, 4, 6, 8, 10, 12, 14, 16\} \\)</span>.  Of these, only one is divisible by 11: the "zero".

You should have all the needed information to finish this problem.  How many numbers of the form <span>\\( ABCDEFG \\)</span> give us a "zero" when we perform the divisibility-by-11 test?  From here, it should not be too hard to compute the probability.

Let <span>\\( x = A + C + E + G \\)</span>, and <span>\\( y = B + D + F \\)</span>.  We are looking for <span>\\( x \\)</span> and <span>\\( y \\)</span> satisfying the linear system:

<div>
	\begin{equation}
	\begin{cases} x + y &amp;= 28 \\ x - y &amp;=0 \end{cases}
	\end{equation}
</div>

The solution gives <span>\\( A + C + E + G = B + D + F = 14 \\)</span>.  We are very close to the punch line.

For example, all the possible triples <span>\\( (B, D, F) \\)</span> satisfying <span>\\( B+D+F = 14 \\)</span> are given below:

<div>
	\begin{equation}
	\begin{array}{cccc} \{ 1, 6, 7 \} &amp; \{ 2,5,7\} &amp; \{ 3,4,7\} &amp; \{3,5,6 \} \end{array}
	\end{equation}
</div>

Let us work with one of those triples, say <span>\\( \{ 1, 6, 7\} \\)</span>.  The possible seven-digit numbers that we can come up with for this choice of <span>\\( \{ B, D, F\} \\)</span> are <span>\\( 3! = 3 \cdot 2 \cdot 1 = 6 \\)</span>:

<div>
	\begin{equation}
	\begin{array}{|c|c|c|} \hline B &amp; D &amp; F \\ \hline  1 &amp; 6 &amp; 7 \\ \hline 1 &amp; 7 &amp; 6 \\ \hline 6 &amp; 1 &amp; 7 \\ \hline 6 &amp; 7 &amp; 1 \\ \hline 7 &amp; 1 &amp; 6 \\ \hline 7 &amp; 6 &amp; 1 \\ \hline \end{array}
	\end{equation}
</div>

We still need to fill in the values for <span>\\( \{ A, C, E, G\} \\)</span>.  In the case we are exploring, we notice that there are <span>\\( 4! = 4 \cdot 3 \cdot 2 \cdot 1 = 24 \\)</span> possibilities for each of the 6 choices above.  For instance, if <span>\\( B=1 \\)</span>, <span>\\( D=6 \\)</span> and <span>\\( F=7 \\)</span>, we would have the numbers

<div>
	\begin{equation}
	\begin{array}{|c|c|c|c|c|c|c|} \hline A &amp; \boldsymbol{B} &amp; C &amp; \boldsymbol{D} &amp; E &amp; \boldsymbol{F} &amp; G \\
	\hline 2 &amp; \boldsymbol{1} &amp; 3 &amp; \boldsymbol{6} &amp; 4 &amp; \boldsymbol{7} &amp; 5 \\
	\hline 2 &amp; \boldsymbol{1} &amp; 3 &amp; \boldsymbol{6} &amp; 5 &amp; \boldsymbol{7} &amp; 4 \\
	\hline 2 &amp; \boldsymbol{1} &amp; 4 &amp; \boldsymbol{6} &amp; 3 &amp; \boldsymbol{7} &amp; 5 \\
	\hline 2 &amp; \boldsymbol{1} &amp; 4 &amp; \boldsymbol{6} &amp; 5 &amp; \boldsymbol{7} &amp; 3 \\
	\hline 2 &amp; \boldsymbol{1} &amp; 5 &amp; \boldsymbol{6} &amp; 3 &amp; \boldsymbol{7} &amp; 5 \\
	\hline 2 &amp; \boldsymbol{1} &amp; 5 &amp; \boldsymbol{6} &amp; 4 &amp; \boldsymbol{7} &amp; 3 \\
	\hline \vdots &amp; \boldsymbol{1} &amp; \vdots &amp; \boldsymbol{6} &amp; \vdots &amp; \boldsymbol{7} &amp; \vdots \\
	\hline 5 &amp; \boldsymbol{1} &amp; 4 &amp; \boldsymbol{6} &amp; 3 &amp; \boldsymbol{7} &amp; 2\\
	\hline \end{array}
	\end{equation}
</div>

So, what is the probability we are looking for?
