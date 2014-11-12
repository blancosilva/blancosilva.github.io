---
layout: post
title: The Cantor Set
date: 2010-10-22 19:29:54.000000000 -04:00
category: post
comments: true
image:
  teaser: http://farm2.static.flickr.com/1155/5105641217_ec5cf35a93_o_d.jpg
---

Consider the unit interval in the real line, <span>\\( [0,1] \\)</span>, and remove the *middle third open subinterval* <span>\\( (1/3, 2/3) \\)</span>.  We have the closed set <span>\\( C_1 = [0,1/3] \cup [2/3,1] \\)</span>, which is the union of two closed intervals.  In a second step, remove the *middle third open subintervals* of each of the previous two intervals in <span>\\( C_1 \\)</span>, to obtain the closed set <span>\\( C_2 = [0,1/9] \cup [2/9,1/3] \cup [2/3, 7/9] \cup [8/9,1] \\)</span>.

The image below illustrates this procedure with the three sets constructed so far.

<img style="margin-rigth:auto; margin-left:auto;" title="Three steps into the Cantor set" src="http://farm2.static.flickr.com/1155/5105641217_ec5cf35a93_o_d.jpg" alt="" />

We iterate this procedure, thus constructing on each step a new closed set <span>\\( C_n \\)</span> by removal of *middle third open subintervals* from the previous set <span>\\( C_{n-1} \\)</span>.  Equivalently, the operation can be described as: *take the union of the previous set, with a shift of it by two units, and scale them down by one-third.*  We can write then <span>\\( C_{n+1} = \frac{1}{3} \big( C_n \cup (2+C_n) \big) \\)</span> for each <span>\\( n \in \mathbb{N}. \\)</span>  Notice that <span>\\( C_{n+1} \subset C_n. \\)</span>

This process is permitted to continue indefinitely.  At the limit, we have removed from the unit interval a countable number of open subintervals; therefore, the resulting set <span>\\( \mathfrak{C} = \cap_{n \in \mathbb{N}} C_n \\)</span> must be closed.  This is what we call the **Cantor set.**

### Structure of the Cantor set

#### Empty?

Notice that the Cantor set is not empty: the numbers <span>\\( 0 \\)</span>, <span>\\( \frac{1}{9} \\)</span>, <span>\\( \frac{2}{9} \\)</span>, <span>\\( \frac{1}{3} \\)</span>, <span>\\( \frac{2}{3} \\)</span>, <span>\\( \frac{7}{9} \\)</span>, <span>\\( \frac{8}{9} \\)</span> and <span>\\( 1 \\)</span> all belong in <span>\\( \mathfrak{C} \\)</span>.  As a matter of fact, if <span>\\( x \in \mathfrak{C} \\)</span>, then either <span>\\( 3x \in \mathfrak{C} \\)</span> or <span>\\( 3x-2 \in \mathfrak{C}, \\)</span> (or both!) which indicates that there are infinitely many elements in the Cantor set.  We will use this fact below.

#### Measure

Let us measure the Cantor set: The unit interval measures one unit.  In the first step, we have removed a subinterval of size <span>\\( \frac{1}{3} \\)</span>; hence, <span>\\( C_1 \\)</span> measures <span>\\( 1 - \frac{1}{3} = \frac{2}{3} \\)</span>.  In the second step, we have removed from <span>\\( C_1 \\)</span> two subintervals of size <span>\\( \frac{1}{9} \\)</span>; hence <span>\\( C_2 \\)</span> measures <span>\\( 1 - \frac{1}{3} - \frac{2}{9} = \frac{4}{9} \\)</span> units. In the <span>\\( n \\)</span>th step, we remove from <span>\\( C_{n-1} \\)</span> as many as <span>\\( 2^{n-1} \\)</span> subintervals of size <span>\\( \frac{1}{3^n} \\)</span>; therefore, the size of <span>\\( C_n \\)</span> is <span>\\( 1 - \sum_{k=1}^n \frac{2^{k-1}}{3^k} \\)</span> units.  At the limit, the Cantor set has therefore size

<div>
\begin{equation}
 1 - \displaystyle{\sum_{k=1}^\infty \frac{1}{2} \bigg( \frac{2}{3} \bigg)^k} = 1 - \frac{1}{2}\cdot \frac{\frac{2}{3}}{1 - \frac{2}{3}} = 0. 
 \end{equation}
</div>

How is that possible?

#### Cardinality

By definition, <span>\\( z \in \mathfrak{C} \\)</span> if and only if <span>\\( z \in C_n \\)</span> for all <span>\\( n \in \mathbb{N}. \\)</span>  This means, in particular, that we can find <span>\\( x \in [0,1] \\)</span> such that  for any <span>\\( n \in \mathbb{N} \\)</span>, there will be an <span>\\( n \\)</span>–tuple <span>\\( (\lambda_1, \lambda_2, \dotsc, \lambda_n) \\)</span> with <span>\\( \lambda_k \in\\{0,2\\} \\)</span> satisfying

<div>
\begin{equation}
 z = \displaystyle{ \frac{x}{3^n} + \frac{1}{3^n} \sum_{k=1}^n 3^{k-1}\lambda_k }. 
 \end{equation}
</div>

Equivalently, for each <span>\\( z \in \mathfrak{C} \\)</span> and any <span>\\( \varepsilon > 0 \\)</span> there is some <span>\\( N=N(z,\varepsilon) \in \mathbb{N} \\)</span> and an <span>\\( N \\)</span>-tuple <span>\\( (\lambda_1, \lambda_2, \dotsc, \lambda_N) \\)</span> with <span>\\( \lambda_k \in \\{0,2\\}, \\)</span> such that <span>\\( \big\lvert z - 3^{-N}\sum_{k=1}^N 3^{k-1}\lambda_k \big\rvert < \varepsilon. \\)</span>   It should be no trouble to prove that this property defines every element of the Cantor set.

For example, consider the sequence <span>\\( \\{ \lambda_n \\}_{n \in \mathbb{N}} \\)</span> with <span>\\( \lambda_{2k}=2 \\)</span> and <span>\\( \lambda_{2k+1}=0 \\)</span> for all <span>\\( k \in \mathbb{N} \\)</span>.  The sequence of partial sums <span>\\( x_n = 3^{-n} \sum_{k=1}^n 3^{k-1}\lambda_k \\)</span> is convergent, with <span>\\( \lim_n x_n = \frac{3}{4}. \\)</span>

Indeed, notice that

<div>
\begin{align} 
x_{2n} &= \displaystyle{3^{-2n}\sum_{k=1}^{2n}3^{k-1}\lambda_{2k}} = \displaystyle{2\cdot 3^{-2n}\sum_{k=1}^n 3^{2k-1}}\\
&= \displaystyle{2\cdot 3^{-2n-1}\sum_{k=1}^n 9^k} = \displaystyle{2\cdot 3^{-2n-1}\frac{9^{n+1}-9}{8}}\\
&= \displaystyle{\frac{3}{4} \bigg(1-\frac{1}{3^{2n}}\bigg)}.
\end{align}
</div>

We have them proven that <span>\\( \frac{3}{4} \\)</span> is in the Cantor set, although it is not the endpoint of any of the removed subintervals in the original construction!

This is an alternative way to describe all numbers in the Cantor set:

> \\( z \in \mathfrak{C} \\) if and only there exists a sequence \\( (\lambda\_n)\_{n \in \mathbb{N}} \\) with \\( \lambda_n \in \\{0,2\\} \\) for all \\( n \in \mathbb{N} \\), such that the partial sum sequence \\( x\_n = 3^{-n} \sum\_{k=1}^n 3^{k-1}\lambda_k \\) converges to \\( z. \\)

We will use this description to construct an injective map <span>\\( \phi \colon [0,1] \to \mathfrak{C}, \\)</span> thus proving that the cardinality of the Cantor set is the same as that of the unit interval (and therefore, the Cantor set is uncountable!)

Let us use the density of dyadic fractions: for each <span>\\( x\in [0,1) \\)</span> and <span>\\( \varepsilon> 0 \\)</span>, find a dyadic number <span>\\( d_{k,n}=k2^{-n} \\)</span> with <span>\\( k \in \\{0,1,2,\dotsc, 2^n-1\\} \\)</span> such that <span>\\( \lvert x-k2^{-n} \rvert < \varepsilon. \\)</span>  We write <span>\\( k \\)</span> in its (unique) base-two expression as <span>\\( k=\mu_0 + 2\mu_1+ \dotsb + 2^{n-1}\mu_{n-1} \\)</span> with values <span>\\( \mu_j \in \\{0,1\\} \\)</span> for all <span>\\( j\in \\{0,1, \dotsc,n-1\\}. \\)</span>  It is then <span>\\( d\_{k,n} = 2^{-n}\sum\_{k=1}^{n-1} 2^k\mu\_k. \\)</span>

A similar reasoning as above shows that any number in the unit interval can be realized as the limit of a partial sum of a sequence <span>\\( x_n = 2^{-n} \sum_{k=0}^{n-1} 2^k\mu_k \\)</span> for a sequence <span>\\( (\mu_n)_{n \in \mathbb{N}} \\)</span> satisfying <span>\\( \mu_k \in \\{0,1\\} \\)</span> for all <span>\\( k \in \mathbb{N}. \\)</span>  We construct the function <span>\\( \phi \colon [0,1] \to \mathfrak{C} \\)</span> as follows:

<div>
\begin{equation}
 [0,1] \ni x \mapsto \bigg( 2^{-n} \sum_{k=0}^{n-1} 2^k\mu_k \bigg)_{n \in \mathbb{N}} \mapsto \bigg( 3^{-n} \sum_{k=0}^{n-1} 3^{k} (2\cdot \mu_k) \bigg)_{n \in \mathbb{N}} \in \mathfrak{C}
 \end{equation}
</div>
