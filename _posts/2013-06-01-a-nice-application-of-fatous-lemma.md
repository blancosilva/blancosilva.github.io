---
layout: post
title: A nice application of Fatou's Lemma
date: 2013-06-01 22:50:28.000000000 -04:00
category: post
comments: true
---

Let me show you an exciting technique to prove some convergence statements using exclusively functional inequalities and Fatou's Lemma. The following are two classic problems solved this way. Enjoy!

> **Exercise 1** *Let \\( {(X, \mathcal{F}, \mu)}\\)  be a measurable space and suppose \\( \\{f_n\\}_{n\in \mathbb{N}} \\)  is a sequence of measurable functions in \\( {L_1(\mu)}\\)  that converge almost everywhere to a function \\( {f \in L_1(\mu)},\\)  and such that the sequence of norms \\( \big\\{ \lVert f_n \rVert_1 \big\\}_{n \in \mathbb{N}} \\)  converges to \\( {\lVert f \rVert_1}\\) . Prove that the sequence of integrals \\( {\int_E \lvert f_n \rvert\, d\mu}\\)  converges to the integral \\( {\int_E \lvert f \rvert\, d\mu}\\)  for every measurable set \\( {E}\\).*

*Proof:*  Note first that

\\[ \displaystyle  \begin{array}{rcl}  \lvert f_n - f\rvert\, \boldsymbol{1}_E \leq \lvert f_n - f \rvert \leq \lvert f_n \rvert + \lvert f \rvert. \end{array}  \\]

Set then \\( {g_n = \lvert f_n \rvert + \lvert f \rvert - \lvert f_n-f \rvert\, \boldsymbol{1}_E} \\) (which are non-negative functions) and apply Fatou's Lemma to that sequence. We have then

<div>
\begin{gather}
\int_X \liminf_n g_n\, d\mu \leq \liminf_n \int_X g_n\, d\mu \\ 
\int_X \liminf_n \big( \lvert f_n \rvert + \lvert f \rvert - \lvert f_n - f \rvert\, \boldsymbol{1}_E \big)\, d\mu \leq \liminf_n \int_X \big( \lvert f_n \rvert + \lvert f \rvert - \lvert f_n - f \rvert\, \boldsymbol{1}_E \big)\, d\mu \\ 
\int_X \big( 2\lvert f \rvert - \limsup_n \lvert f_n-f \rvert\, \boldsymbol{1}_E\big)\, d\mu \leq \liminf_n \int_X \lvert f_n \rvert\, d\mu + \lVert f \rVert_1 - \limsup_n \int_E \lvert f_n -f \rvert\, d\mu \\ 
2\lVert f\rVert_1 \leq 2\lVert f \rVert_1 - \limsup_n \int_E \lvert f_n - f\rvert\, d\mu,
\end{gather}
</div>

which implies

\\( \displaystyle  \begin{array}{rcl}  0 \leq \liminf_n \int_E \lvert f_n-f \rvert\, d\mu \leq \limsup_n \int_E \lvert f_n-f \rvert\, d\mu \leq 0. \end{array}  \\)

It must then be \\( {\int_E \lvert f_n - f \rvert\, d\mu = 0} \\). But this proves the statement, since

\\( \displaystyle  \begin{array}{c}  \bigg\lvert \int_E \lvert f_n\rvert\, d\mu - \int_E \lvert f \rvert\, d\mu \bigg\rvert = \bigg\lvert \int_E \big( \lvert f_n \rvert - \lvert f \rvert \big)\, d\mu \bigg\rvert \\  \leq \int_E \Big\lvert \lvert f_n \rvert - \lvert f \rvert \Big\rvert\, d\mu \leq \int_E \lvert f_n - f \rvert\, d\mu \end{array}  \\)

\\( \Box \\)

> **Exercise 2** * Let \\( {(X, \mathcal{F}, \mu)}\\)  be a finite measure space and let \\( {1&lt;p&lt;\infty}\\) . Suppose that \\( {\{ f_n \}_{n \in \mathbb{N}}}\\)  is a sequence of measurable functions in \\( {L_p(\mu)}\\)  whose norms are uniformly bounded in \\( {n}\\)  and which converge almost everywhere to a function \\( {f}\\) . Prove that the sequence \\( {\big\{ \int_X f_ng\, d\mu \big\}_{n \in \mathbb{N}}}\\)  converges to \\( {\int_x fg\, d\mu}\\)  for all \\( {g \in L_q(\mu)}\\)  where \\( {q}\\)  is the conjugate exponent of \\( {p}\\) . *

*Proof:*  The proof is very similar to the previous problem. We start by noticing that under the hypotheses of the problem,

\\( \displaystyle  \begin{array}{c}  \bigg\lvert \int_x f_ng\, d\mu - \int_X fg\, d\mu \bigg\rvert = \bigg\lvert \int_X (f_n -f)g\, d\mu \bigg\rvert \\ \leq \lVert (f_n-f)g \rVert_1 \leq \lVert f_n - f \rVert_p\, \lVert g \rVert_q. \end{array}  \\)

If we prove that \\( {\lim_n \lVert f_n-f \rVert_p = 0} \\), we are done.

We will achieve this by using the convexity of \\( {\lvert \cdot \rvert^p} \\), since in that case it is

\\( \displaystyle  \begin{array}{rcl}  \frac{\lvert f_n - f \rvert^p}{2^p} \leq \tfrac{1}{2} \lvert f_n \rvert^p + \tfrac{1}{2} \lvert f \rvert^p. \end{array}  \\)

hence,

\\( \displaystyle  \begin{array}{rcl}  \lvert f_n -f \rvert^p \leq 2^{p-1} \big( \lvert f_n \rvert^p + \lvert f \rvert^p \big). \end{array}  \\)

Set then \\( {g_n = 2^{p-1} \big( \lvert f_n\rvert^p + \lvert f \rvert^p\big) - \lvert f_n-f \rvert^p} \\) (which are non-negative functions) and apply Fatou's Lemma as before. \\( \Box \\)

